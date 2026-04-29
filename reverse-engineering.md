# Reverse Engineering — Complete Specification

## Overview

This document provides comprehensive coverage of reverse engineering techniques, tools, and methodologies for binary analysis, malware analysis, and CTF challenges for the AEHM dataset.

**Target examples:** 4M
**MITRE focus:** T1027, T1140

---

## Table of Contents

1. [Binary Analysis Fundamentals](#1-binary-analysis-fundamentals)
2. [Tools & Techniques](#2-tools--techniques)
3. [CTF-Oriented RE](#3-ctf-oriented-re)
4. [Advanced RE Techniques](#4-advanced-re-techniques)
5. [Platform-Specific RE](#5-platform-specific-re)

---

## 1. Binary Analysis Fundamentals

### 1.1 x86/x64 Assembly
- x86/x64 assembly fundamentals for RE
- Registers and their usage
- Memory addressing modes
- Stack frame analysis
- Heap frame analysis
- Calling conventions — cdecl, stdcall, fastcall, thiscall
- Function prologues/epilogues
- Loop structure recognition
- Switch statement patterns
- Conditional jump patterns
- Arithmetic operations

### 1.2 Control Flow Analysis
- Basic block identification
- Control flow graph construction
- Dominator analysis
- Loop detection
- Recursion detection
- Tail call optimization detection
- Inline function detection
- Function inlining detection
- Branch prediction analysis
- Control flow obfuscation

### 1.3 Data Flow Analysis
- Variable tracking
- Register tracking
- Stack variable tracking
- Heap variable tracking
- Constant propagation
- Copy propagation
- Dead code elimination
- Live variable analysis
- Reaching definitions
- Available expressions

### 1.4 String Analysis
- String reference analysis
- String reconstruction
- String decoding
- String encryption
- String obfuscation
- String compression
- String format analysis
- String encoding detection
- String character set analysis
- String localization

### 1.5 Cross-Reference Analysis
- Function cross-references
- Data cross-references
- Import cross-references
- Export cross-references
- String cross-references
- Resource cross-references
- Registry cross-references
- File cross-references
- Network cross-references
- API cross-references

### 1.6 Symbol Recovery
- Symbol recovery without debug info
- PDB file analysis
- Symbol server access
- Symbol file parsing
- Symbol name reconstruction
- Symbol type reconstruction
- Symbol signature matching
- Symbol database lookup
- Symbol server caching
- Symbol version management

### 1.7 Type Reconstruction
- Type reconstruction from assembly
- Structure reconstruction
- Class reconstruction
- Union reconstruction
- Array reconstruction
- Pointer reconstruction
- Function signature reconstruction
- Variable type reconstruction
- Return type reconstruction
- Parameter type reconstruction

---

## 2. Tools & Techniques

### 2.1 Disassemblers & Decompilers

#### Ghidra
- Ghidra full workflow
- Ghidra scripting API
- Ghidra headless analysis
- Ghidra plugin development
- Ghidra PDB integration
- Ghidra symbol server
- Ghidra version tracking
- Ghidra collaborative analysis
- Ghidra script development
- Ghidra extension development

#### IDA Pro
- IDA Pro shortcuts
- IDA Pro scripts
- IDA Pro FLIRT signatures
- IDA Pro debugger
- IDA Pro Python API
- IDA Pro IDC scripts
- IDA Pro plugins
- IDA Pro Hex-Rays
- IDA Pro decompiler
- IDA Pro remote debugging

#### Binary Ninja
- Binary Ninja IL analysis
- Binary Ninja API
- Binary Ninja plugins
- Binary Ninja scripting
- Binary Ninja decompiler
- Binary Ninja debugger
- Binary Ninja cloud
- Binary Ninja collaboration
- Binary Ninja signatures
- Binary Ninja automation

#### Radare2
- Radare2 command-line RE
- Radare2 visual mode
- Radare2 scripting
- Radare2 plugins
- Radare2 debugger
- Radare2 decompiler
- Radare2 signatures
- Radare2 analysis
- Radare2 collaboration
- Radare2 automation

### 2.2 Debuggers

#### x64dbg / WinDbg
- x64dbg dynamic analysis
- WinDbg dynamic analysis
- WinDbg commands
- WinDbg extensions
- WinDbg scripting
- WinDbg symbols
- WinDbg memory analysis
- WinDbg process analysis
- WinDbg thread analysis
- WinDbg kernel debugging

#### GDB
- GDB with PEDA/GEF/pwndbg: Linux binary
- GDB commands
- GDB scripting
- GDB plugins
- GDB Python API
- GDB TUI mode
- GDB remote debugging
- GDB core dump analysis
- GDB process tracing
- GDB breakpoint management
- GDB watchpoint management

### 2.3 Dynamic Instrumentation

#### ltrace / strace
- ltrace library tracing
- strace system call tracing
- System call analysis
- Library call analysis
- Function call analysis
- Parameter analysis
- Return value analysis
- Error code analysis
- Performance analysis
- Behavior analysis

#### Frida
- Frida dynamic instrumentation scripts
- Frida hooking
- Frida tracing
- Frida memory manipulation
- Frida function replacement
- Frida object manipulation
- Frida class manipulation
- Frida method manipulation
- Frida SSL pinning bypass
- Frida root detection bypass

### 2.4 Symbolic Execution
- angr symbolic execution — full examples
- angr constraint solving
- angr path exploration
- angr memory modeling
- angr function modeling
- angr loop handling
- angr symbolic memory
- angr concrete execution
- angr mixed execution
- angr vulnerability detection

### 2.5 Binary Diffing
- Diaphora binary diffing
- BinDiff binary diffing
- DarunGrim binary diffing
- Radare2 diffing
- Ghidra diffing
- IDA Pro diffing
- Patch diffing
- Version diffing
- Function diffing
- Code diffing

---

## 3. CTF-Oriented RE

### 3.1 Crackme Challenges
- Crackme challenges — methodology
- Serial number generation
- License key validation
- Password verification
- Time-based challenges
- Network-based challenges
- File-based challenges
- Memory-based challenges
- Registry-based challenges
- Hardware-based challenges

### 3.2 Anti-Debugging Bypass
- Anti-debugging bypass collection
- Debugger detection bypass
- Breakpoint detection bypass
- Single-step detection bypass
- Trace detection bypass
- Hardware breakpoint bypass
- Software breakpoint bypass
- Memory breakpoint bypass
- Register breakpoint bypass
- Exception-based detection bypass

### 3.3 Obfuscated Code Deobfuscation
- Obfuscated code deobfuscation
- Control flow flattening
- Code virtualization
- String obfuscation
- API obfuscation
- Control flow obfuscation
- Data obfuscation
- Binary encryption
- Binary compression
- Code mutation

### 3.4 Custom Encoding/Encryption
- Custom encoding reversal
- Custom encryption reversal
- Custom compression reversal
- Custom hashing reversal
- Custom checksum reversal
- Custom CRC reversal
- Custom XOR reversal
- Custom substitution reversal
- Custom permutation reversal
- Custom transformation reversal

### 3.5 Virtual Machine Obfuscation
- VM obfuscation analysis
- VM bytecode analysis
- VM handler analysis
- VM context analysis
- VM stack analysis
- VM memory analysis
- VM register analysis
- VM instruction analysis
- VM execution analysis
- VM deobfuscation

### 3.6 Packer Unpacking
- Packer unpacking methodology
- UPX unpacking
- Themida unpacking
- VMProtect unpacking
- Armadillo unpacking
- ASProtect unpacking
- NSPack unpacking
- Petite unpacking
- PECompact unpacking
- MoleBox unpacking

### 3.7 License Key Algorithm
- License key algorithm reversal
- Key generation algorithm
- Key validation algorithm
- Key format analysis
- Key checksum analysis
- Key encryption analysis
- Key encoding analysis
- Key obfuscation analysis
- Key distribution analysis
- Key revocation analysis

### 3.8 Serial Number Generation
- Serial number generation reversal
- Serial number format analysis
- Serial number validation
- Serial number checksum
- Serial number encryption
- Serial number encoding
- Serial number obfuscation
- Serial number distribution
- Serial number verification
- Serial number bypass

---

## 4. Advanced RE Techniques

### 4.1 Firmware Analysis
- Firmware extraction
- Firmware unpacking
- Firmware deobfuscation
- Firmware disassembly
- Firmware debugging
- Firmware emulation
- Firmware modification
- Firmware patching
- Firmware signing
- Firmware verification

### 4.2 Kernel Analysis
- Kernel driver analysis
- Kernel module analysis
- Kernel hooking analysis
- Kernel rootkit analysis
- Kernel exploit analysis
- Kernel vulnerability analysis
- Kernel debugging
- Kernel emulation
- Kernel patching
- Kernel verification

### 4.3 Mobile RE
- Android APK analysis
- Android DEX analysis
- Android SO analysis
- Android OAT analysis
- Android VDEX analysis
- iOS IPA analysis
- iOS Mach-O analysis
- iOS dyld analysis
- iOS dylib analysis
- iOS kernelcache analysis

### 4.4 Embedded Systems RE
- Embedded firmware extraction
- Embedded firmware analysis
- Embedded debugging
- Embedded emulation
- Embedded patching
- Embedded modification
- Embedded exploitation
- Embedded vulnerability analysis
- Embedded protocol analysis
- Embedded communication analysis

### 4.5 GPU RE
- GPU shader analysis
- GPU kernel analysis
- GPU bytecode analysis
- GPU assembly analysis
- GPU debugging
- GPU emulation
- GPU patching
- GPU optimization
- GPU vulnerability analysis
- GPU exploitation

### 4.6 Hypervisor RE
- Hypervisor analysis
- Virtual machine monitor analysis
- Hypervisor debugging
- Hypervisor emulation
- Hypervisor patching
- Hypervisor modification
- Hypervisor exploitation
- Hypervisor vulnerability analysis
- Hypervisor escape analysis
- Hypervisor detection

---

## 5. Platform-Specific RE

### 5.1 Windows RE
- PE file format analysis
- Windows API analysis
- Windows registry analysis
- Windows service analysis
- Windows driver analysis
- Windows kernel analysis
- Windows COM analysis
- Windows .NET analysis
- Windows WMI analysis
- Windows PowerShell analysis

### 5.2 Linux RE
- ELF file format analysis
- Linux syscall analysis
- Linux library analysis
- Linux kernel module analysis
- Linux kernel analysis
- Linux systemd analysis
- Linux D-Bus analysis
- Linux container analysis
- Linux hypervisor analysis
- Linux firmware analysis

### 5.3 macOS RE
- Mach-O file format analysis
- macOS framework analysis
- macOS dylib analysis
- macOS kernel extension analysis
- macOS kernel analysis
- macOS SIP analysis
- macOS TCC analysis
- macOS Gatekeeper analysis
- macOS code signing analysis
- macOS notarization analysis

### 5.4 Android RE
- APK file format analysis
- DEX file format analysis
- Android runtime analysis
- Android framework analysis
- Android native library analysis
- Android kernel analysis
- Android hypervisor analysis
- Android TrustZone analysis
- Android bootloader analysis
- Android firmware analysis

### 5.5 iOS RE
- IPA file format analysis
- Mach-O file format analysis
- iOS framework analysis
- iOS dylib analysis
- iOS kernel analysis
- iOS kernel extension analysis
- iOS Secure Enclave analysis
- iOS TrustZone analysis
- iOS bootloader analysis
- iOS firmware analysis

---

*End of Reverse Engineering Specification*
