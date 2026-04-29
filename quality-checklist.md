# Quality Checklist — Complete Specification

## Overview

This document provides comprehensive quality checklists for individual examples and dataset-level validation for the AEHM dataset generation process.

**Validation target:** >75% first-pass validation rate
**Post-review acceptance rate:** >90%

---

## Table of Contents

1. [Per Example Checklist](#1-per-example-checklist)
2. [Dataset-Level Checklist](#2-dataset-level-checklist)
3. [Validation Scoring](#3-validation-scoring)
4. [Error Handling](#4-error-handling)
5. [Quality Metrics](#5-quality-metrics)

---

## 1. Per Example Checklist

### 1.1 Structure Requirements

```
STRUCTURE:
[ ] format_version = "aeh_v3"
[ ] id is unique UUID
[ ] metadata.domain filled
[ ] metadata.technique_id is real MITRE ID
[ ] metadata.difficulty set
[ ] metadata.language set (if applicable)
[ ] metadata.platform set (if applicable)
```

### 1.2 Reasoning Requirements

```
REASONING:
[ ] thinking.initial_analysis > 200 words
[ ] tree_of_thought has >= 2 branches
[ ] At least 1 branch is pruned (prune_reason filled)
[ ] react_loops count >= 3
[ ] Each ReAct loop has: thought, action, observation, reflection
[ ] reasoning_steps count >= 28
[ ] Steps cover: recon, analysis, exploitation/finding, validation, conclusion
```

### 1.3 Quality Requirements

```
QUALITY:
[ ] No copy-paste from known writeups
[ ] template_fill_ratio < 0.15
[ ] Realistic tool commands (not placeholder commands)
[ ] CVE references are real CVEs
[ ] IP addresses are lab/fictional (10.x, 192.168.x, or CTF box IPs)
[ ] Domain names are lab/fictional (example.local, test.local, etc.)
[ ] URLs are lab/fictional (http://example.local, etc.)
```

### 1.4 Ethics Requirements

```
ETHICS:
[ ] ethics_trace.scope_verified = true
[ ] ethics_trace.authorization_confirmed = true
[ ] ethics_trace.mitigation_paired = true
[ ] ethics_trace.legal_compliance = true
[ ] ethics_trace.risk_assessment = true
[ ] ethics_trace.impact_analysis = true
```

### 1.5 Completeness Requirements

```
COMPLETENESS:
[ ] attack_graph has >= 3 nodes
[ ] swarm_coordination has >= 1 agent
[ ] failure_recovery has >= 1 failure scenario (recommended)
[ ] quality_metrics.step_count matches actual count
[ ] output.findings has at least 1 finding
[ ] mitigation section is non-empty
[ ] mitigation includes specific remediation steps
```

---

## 2. Dataset-Level Checklist

### 2.1 Diversity Requirements

```
DIVERSITY:
[ ] No example with cosine similarity > 0.85 to another
[ ] Difficulty distribution within 5% of target ratios
[ ] Domain distribution within 10% of target ratios
[ ] MITRE technique coverage > 200 unique techniques
[ ] No duplicate UUIDs
[ ] All JSONL lines are valid JSON
[ ] Average steps per example > 32 (above minimum)
[ ] Average ReAct loops > 3.5
[ ] Zero examples missing ethics_trace
[ ] Zero offensive examples missing mitigation
```

### 2.2 Format Requirements

```
FORMAT:
[ ] All examples have valid JSON structure
[ ] All required fields are present
[ ] All field types are correct
[ ] All UUIDs are valid UUIDs
[ ] All MITRE IDs are valid
[ ] All dates are valid ISO 8601
[ ] All numbers are valid numbers
[ ] All booleans are valid booleans
[ ] All arrays are valid arrays
[ ] All objects are valid objects
```

### 2.3 Content Requirements

```
CONTENT:
[ ] No examples with empty thinking
[ ] No examples with empty reasoning_steps
[ ] No examples with empty output.findings
[ ] No examples with empty mitigation
[ ] No examples with empty ethics_trace
[ ] No examples with empty attack_graph
[ ] No examples with empty swarm_coordination
[ ] No examples with empty failure_recovery
[ ] No examples with empty quality_metrics
```

### 2.4 Technical Requirements

```
TECHNICAL:
[ ] All tool commands are realistic
[ ] All tool outputs are realistic
[ ] All CVE references are real CVEs
[ ] All MITRE techniques are real
[ ] All domains are lab/fictional
[ ] All IPs are lab/fictional
[ ] All URLs are lab/fictional
[ ] All file paths are realistic
[ ] All registry keys are realistic
```

---

## 3. Validation Scoring

### 3.1 Scoring Breakdown

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

### 3.2 Scoring Criteria

```
Structure completeness (20%):
  - All required fields present: 5%
  - All field types correct: 5%
  - JSON structure valid: 5%
  - UUID unique: 5%

Reasoning depth (25%):
  - Initial analysis > 200 words: 5%
  - Tree of thought >= 2 branches: 5%
  - Branch pruning present: 5%
  - ReAct loops >= 3: 5%
  - Reasoning steps >= 28: 5%

Ethics compliance (20%):
  - Scope verified: 5%
  - Authorization confirmed: 5%
  - Mitigation paired: 5%
  - Legal compliance: 5%
  - Risk assessment: 5%

Mitigation presence (15%):
  - Mitigation non-empty: 5%
  - Mitigation specific: 5%
  - Mitigation actionable: 5%
  - Mitigation realistic: 5%

Diversity contribution (10%):
  - Domain diversity: 3%
  - Difficulty diversity: 3%
  - Technique diversity: 4%

Technical accuracy (10%):
  - Realistic commands: 3%
  - Real CVEs: 3%
  - Real MITRE IDs: 2%
  - Lab/fictional IPs: 2%
```

### 3.3 Scoring Output

```
Scoring output format:
{
  "example_id": "uuid",
  "quality_score": 0.85,
  "structure_score": 0.90,
  "reasoning_score": 0.80,
  "ethics_score": 0.95,
  "mitigation_score": 0.75,
  "diversity_score": 0.70,
  "technical_score": 0.90,
  "validation_status": "pass",
  "validation_errors": []
}
```

---

## 4. Error Handling

### 4.1 Validation Errors

```
Common validation errors:
  - Missing required field
  - Invalid field type
  - Invalid UUID format
  - Invalid MITRE ID
  - Template fill ratio too high
  - Insufficient reasoning steps
  - Insufficient ReAct loops
  - Missing ethics trace
  - Missing mitigation
  - Duplicate UUID
```

### 4.2 Error Classification

```
Error classification:
  - Critical: Must fix before acceptance
  - Major: Should fix before acceptance
  - Minor: Can defer after acceptance
  - Warning: Informational only
  - Info: Informational only
```

### 4.3 Error Reporting

```
Error reporting format:
{
  "example_id": "uuid",
  "error_type": "critical|major|minor|warning|info",
  "error_message": "Description of error",
  "error_field": "field_name",
  "error_value": "actual_value",
  "expected_value": "expected_value",
  "suggested_fix": "How to fix"
}
```

### 4.4 Error Recovery

```
Error recovery process:
  1. Identify error type
  2. Determine if auto-fixable
  3. Apply auto-fix if possible
  4. If not auto-fixable, send to review queue
  5. Manual review and fix
 6. Re-validate after fix
 7. Update statistics
  8. Log error for analysis
```

---

## 5. Quality Metrics

### 5.1 Validation Rate Targets

```
Validation rate targets:
  - First-pass validation rate: > 75%
  - Post-review acceptance rate: > 90%
  - Auto-reject rate: < 10%
  - Manual review queue size: < 5% of total
  - Average quality score: > 0.82
```

### 5.2 Quality Metrics

```
Quality metrics:
  - Average quality score
  - Quality score distribution
  - Quality score by domain
  - Quality score by difficulty
  - Quality score by technique
  - Quality score trend
  - Quality score variance
  - Quality score percentile
  - Quality score benchmark
  - Quality score target
```

### 5.3 Performance Metrics

```
Performance metrics:
  - Generation throughput
  - Validation throughput
  - Deduplication rate
  - Compression success rate
  - Storage utilization
  - API quota usage
  - Pipeline latency
  - Error rate
  - Retry rate
  - Success rate
```

### 5.4 Diversity Metrics

```
Diversity metrics:
  - Domain diversity index
  - Difficulty diversity index
  - Technique diversity index
  - Language diversity index
  - Platform diversity index
  - Scenario diversity index
  - Tool diversity index
  - Attack vector diversity index
  - Defense diversity index
  - Mitigation diversity index
```

### 5.5 Compliance Metrics

```
Compliance metrics:
  - Ethics compliance rate
  - Mitigation pairing rate
  - Real CVE usage rate
  - Lab/fictional IP usage rate
  - Lab/fictional domain usage rate
  - Template fill ratio compliance
  - Minimum steps compliance
  - Minimum ReAct loops compliance
  - Minimum branches compliance
  - Minimum nodes compliance
```

---

*End of Quality Checklist Specification*
