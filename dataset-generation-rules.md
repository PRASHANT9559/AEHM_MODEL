# Dataset Generation Rules — Complete Specification

## Overview

This document provides detailed rules, templates, and validation procedures for generating the AEHM dataset according to the roadmap specifications.

**Target:** 40M–107M examples
**Validation target:** >75% first-pass validation rate

---

## Table of Contents

1. [Windsurf Batch Template](#1-windsurf-batch-template)
2. [Quality Validation](#2-quality-validation)
3. [n8n Pipeline Flow](#3-n8n-pipeline-flow)
4. [Deduplication Process](#4-deduplication-process)
5. [Statistics Reporting](#5-statistics-reporting)

---

## 1. Windsurf Batch Template

### 1.1 Batch Configuration

```
Batch size: 50 examples per generation run
Per batch requirements:
  - Min 5 different domains
  - Min 5 different difficulty levels
  - Min 10 different MITRE technique IDs
  - Min 15 examples with failure+recovery scenarios
  - Min 20 examples with 4+ ReAct loops (not just minimum 3)
  - ALL examples: full ethics trace + mitigation

Diversity enforcement:
  - No two examples with same target tech + same technique
  - If same domain: must differ in attack vector or defense
  - Random seed rotation: vary scenario contexts
```

### 1.2 Batch Generation Process

```
1. Initialize batch with random seed
2. Select domains (min 5 different)
3. Select difficulties (min 5 different)
4. Select MITRE techniques (min 10 different)
5. Generate examples with diversity constraints
6. Validate each example against checklist
7. Retry failed examples (max 3 attempts)
8. Remove failed examples after max retries
9. Ensure batch meets minimum requirements
10. Submit batch for validation
```

### 1.3 Random Seed Management

```
Seed rotation strategy:
  - Use cryptographically secure random seed
  - Rotate seed every batch
  - Document seed for reproducibility
  - Maintain seed history for debugging
  - Avoid seed collision
  - Use seed for deterministic testing
```

---

## 2. Quality Validation

### 2.1 Validation Prompt Structure

```
Validation Prompt Structure:
  1. Check format_version field
  2. Count react_loops (reject if < 3)
  3. Count reasoning_steps (reject if < 28)
  4. Check ethics_trace.scope_verified = true
  5. Check mitigation section exists and is non-empty
  6. Calculate template_fill_ratio (reject if > 0.15)
  7. Check tree_of_thought has 2+ branches
  8. Verify at least 1 branch is pruned (SABER)
  9. Check attack_graph has 3+ nodes
  10. Verify MITRE technique ID is real
```

### 2.2 Validation Scoring

```
Quality score calculation:
  - Structure completeness: 20%
  - Reasoning depth: 25%
  - Ethics compliance: 20%
  - Mitigation presence: 15%
  - Diversity contribution: 10%
  - Technical accuracy: 10%

Pass threshold: > 0.75
Review threshold: 0.60-0.75
Reject threshold: < 0.60
```

### 2.3 Validation API Integration

```
Validation API endpoints:
  - POST /validate — single example validation
  - POST /batch-validate — batch validation
  - GET /validation-status — check validation status
  - GET /validation-report — validation report
  - POST /revalidate — re-validate failed examples

API rate limiting:
  - 100 requests per minute per API key
  - 1000 requests per hour per API key
  - 10000 requests per day per API key
```

---

## 3. n8n Pipeline Flow

### 3.1 Pipeline Architecture

```
Windsurf generates batch (50 .aeh files)
         ↓
n8n webhook receives JSON array
         ↓
Split: individual examples
         ↓
Parallel validation (4 Gemini Flash API keys, round-robin)
         ↓
Pass (quality_score > 0.75): → Append to master JSONL
Fail (quality_score < 0.75): → Review queue
         ↓
Every 10K examples: run deduplication (cosine similarity < 0.85)
         ↓
Every 100K examples: run statistics report
         ↓
Nightly: convert JSONL → Parquet + LZ4 compress
```

### 3.2 Error Handling

```
Error handling strategy:
  - Validation timeout: retry with exponential backoff
  - API rate limit: queue and retry
  - Invalid JSON: log and reject
  - Parse error: log and reject
  - Validation failure: send to review queue
  - Deduplication failure: log and reject
  - Compression failure: log and retry
  - Storage failure: log and alert
```

### 3.3 Monitoring

```
Pipeline monitoring:
  - Batch generation rate
  - Validation throughput
  - Validation success rate
  - Validation error rate
  - Review queue size
  - Deduplication rate
  - Compression success rate
  - Storage utilization
  - API quota usage
  - Pipeline latency
```

---

## 4. Deduplication Process

### 4.1 Deduplication Strategy

```
Deduplication parameters:
  - Cosine similarity threshold: 0.85
  - Batch size: 10K examples
  - Embedding model: text-embedding-004
  - Chunk size: 1000 characters
  - Overlap: 200 characters
  - Similarity metric: cosine
```

### 4.2 Deduplication Process

```
Deduplication steps:
  1. Load batch of 10K examples
  2. Extract text fields (thinking, reasoning_steps, output)
  3. Generate embeddings for each example
  4. Calculate pairwise cosine similarity
 5. Identify pairs with similarity > 0.85
  6. Keep higher quality example (based on quality_score)
 7. Remove lower quality example
  8. Log deduplication statistics
  9. Update deduplication report
  10. Continue with remaining examples
```

### 4.3 Deduplication Reporting

```
Deduplication report contents:
  - Total examples processed
  - Duplicate pairs found
  - Examples removed
  - Examples retained
  - Similarity distribution
  - Domain-specific deduplication
  - Difficulty-specific deduplication
  - Technique-specific deduplication
  - Time-based deduplication
  - Storage savings
```

---

## 5. Statistics Reporting

### 5.1 Statistics Frequency

```
Statistics reporting schedule:
  - Every 100K examples: detailed report
  - Every 1M examples: comprehensive report
  - End of each phase: phase completion report
  - Weekly: weekly summary report
  - Monthly: monthly summary report
  - On demand: custom report
```

### 5.2 Statistics Metrics

```
Statistics metrics:
  - Total examples generated
  - Total examples validated
  - Total examples accepted
  - Total examples rejected
  - Validation success rate
  - Average quality score
  - Quality score distribution
  - Domain distribution
  - Difficulty distribution
  - MITRE technique distribution
  - ReAct loop distribution
  - Reasoning step distribution
  - Ethics trace compliance
  - Mitigation presence
  - Template fill ratio
  - Deduplication rate
  - Generation throughput
  - Validation throughput
```

### 5.3 Statistics Reporting Format

```
Statistics report format:
  - Executive summary
  - Detailed metrics
  - Domain breakdown
  - Difficulty breakdown
  - Technique breakdown
  - Quality analysis
  - Error analysis
  - Performance analysis
  - Recommendations
  - Next steps
```

---

*End of Dataset Generation Rules Specification*
