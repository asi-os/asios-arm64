
# 🚀 ASIOS™ ARM64 Optimizations & Drivers
[![Sponsor](https://img.shields.io/github/sponsors/asi-os?label=Sponsor&logo=github)](https://github.com/sponsors/asi-os)

The **ASIOS™ ARM64** repository contains architecture-specific code, drivers, and performance optimizations for 64-bit ARM platforms (NVIDIA Grace, AWS Graviton, Apple Silicon, etc.).

---

## 🧠 Overview

- **Kernel Patches & Modules**  
  - Scheduling tweaks for big.LITTLE and heterogeneous cores  
  - NUMA balancing tuned to ARM memory hierarchies  
  - Low-latency I/O adjustments for CXL and high-speed interconnects  

- **Drivers & Firmware Helpers**  
  - SPI/I²C drivers for board-specific sensors and power management  
  - GPUDirect RDMA glue layers for ARM-hosted NVIDIA GPUs  
  - Early-boot hooks for secure-boot and trusted-boot  

- **Performance Tuning**  
  - Auto-tuner profiles for TensorFlow/PyTorch on ARM  
  - Hugepage and cache-partitioning scripts  
  - Dynamic power-profile management utilities  

---

## 🛠️ Prerequisites

**Hardware**  
- Native ARM64 server (e.g. NVIDIA Grace, AWS Graviton, Apple M1/M2)  
- QEMU/AArch64 emulation (optional)  

**Software**  
- Ubuntu 24.04 LTS HWE (arm64) or equivalent  
- Build tools: `gcc-aarch64-linux-gnu`, `make`, `git`, `libnuma-dev`

```bash
sudo apt update
sudo apt install -y gcc-aarch64-linux-gnu make git libnuma-dev
```

---

## 🏗️ Build & Test

1. **Clone**  
   ```bash
   git clone https://github.com/asi-os/asios-arm64.git
   cd asios-arm64
   ```

2. **(Optional) Cross-compile**  
   ```bash
   export ARCH=arm64
   export CROSS_COMPILE=aarch64-linux-gnu-
   ```

3. **Build**  
   ```bash
   make -j$(nproc)
   ```

4. **Install & Load**  
   ```bash
   sudo make install
   sudo modprobe asios_arm64_scheduler
   ```

5. **Test**  
   ```bash
   make test
   ./benchmarks/run_arm64_perf.sh
   ./scripts/qemu_test.sh
   ```

---

## 📚 Documentation

See the central **ASIOS™ Docs** for detailed guides and roadmap:  
- [ARCHITECTURE.md](https://github.com/asi-os/asios-docs/blob/main/ARCHITECTURE.md)  
- [ROADMAP.md](https://github.com/asi-os/asios-docs/blob/main/ROADMAP.md)  
- [CHANGELOG.md](https://github.com/asi-os/asios-docs/blob/main/CHANGELOG.md)  
- `asios-docs/ADR/` directory in the same repo  

---

## 🤝 Contributing

Before you contribute:  
1. Sign the [ICLA](https://github.com/asi-os/asios-legal/blob/main/ICLA.md) via the CLA Assistant  
2. Add a DCO line to each commit:  
   ```bash
   git commit -s -m "Your description"
   ```

Then:  
- Open an Issue in this repo  
- Submit a PR per [CONTRIBUTING.md](https://github.com/asi-os/.github/blob/main/CONTRIBUTING.md)  

Join our Discord community → <https://discord.gg/rWuU7cWU4E>  
