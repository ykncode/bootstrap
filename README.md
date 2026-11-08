# 🌱 Yukinary Stage-0 C++ Bootstrap Seed

Standalone, single-file C++17 bootstrap engine for the **Yukinary Programming Language**.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE-MIT)
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE-APACHE)
[![Compiler: Yukinary](https://img.shields.io/badge/Main_Repository-ykncode/yukinary-brightgreen)](https://github.com/ykncode/yukinary)

---

## 📌 Purpose

Yukinary is a **self-hosting** language: its main compiler (`src/`) is written in 100% pure Yukinary.

This repository contains **Stage-0 (`app_full.cpp`)**: a self-contained, single-file C++17 implementation that acts as the initial "seed" to compile the Yukinary self-hosted compiler on platforms where pre-compiled native binaries are not yet available.

> **Note:** If pre-compiled binaries exist for your operating system (Windows x86-64 or Linux x86-64), you **do not need** this repository. Download the standalone `ykn.exe` or `ykn` binary directly from [Yukinary Releases](https://github.com/ykncode/yukinary/releases).

---

## 🛠️ Building Stage-0

### Windows (MinGW GCC / Clang)
```powershell
g++ -O2 -std=c++17 -o ykn_bootstrap.exe app_full.cpp -lws2_32
.\ykn_bootstrap.exe --surum
```

### Windows (MSVC)
```cmd
cl /O2 /std:c++17 /Fe:ykn_bootstrap.exe app_full.cpp ws2_32.lib
```

### Linux (GCC / Clang)
```bash
g++ -O2 -std=c++17 -o ykn_bootstrap app_full.cpp -lpthread
chmod +x ykn_bootstrap
./ykn_bootstrap --surum
```

---

## 🚀 Bootstrapping the Main Compiler

Once `ykn_bootstrap` is compiled, clone the main repository and build Stage-1:

```bash
git clone https://github.com/ykncode/yukinary.git
cd yukinary

# Compile Stage-1 using the bootstrap compiler
../ykn_bootstrap src/main.ykn -o ykn_stage1.exe

# Verify fixpoint: Stage-1 compiling Stage-2
./ykn_stage1.exe src/main.ykn -o ykn_stage2.exe
```

---

## 📜 License

Dual-licensed under either of:
* Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE))
* MIT license ([LICENSE-MIT](LICENSE-MIT))

at your option.
