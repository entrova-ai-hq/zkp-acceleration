# zkp-acceleration

**Optimized CPU–GPU collaborative acceleration of zero-knowledge proofs for confidential transactions**

---

## 🧪 Test 1: Throughput of ZKP Generation (Transactions per Second)

**🎯 Objective**: Measure the rate at which ZKPs for confidential transactions can be generated using CPU–GPU collaboration.

### 🛠️ Setup
- Implement a ZKP protocol (e.g., zk-SNARKs or Bulletproofs) for a simplified confidential transaction.
- Use 3–5 H100 GPUs in parallel.
- CPU handles preprocessing (e.g., witness generation); GPUs perform proof computations (e.g., FFTs, EC operations).
- Generate a dataset of 10,000 transactions.

### ▶️ Execution
- Run workloads with batch sizes of 100, 500, and 1000 transactions.
- CPU prepares inputs; GPUs compute proofs concurrently.

### 📊 Metrics
- **Transactions per Second (TPS)**: Target 100–500 TPS based on batch size.
- **GPU Utilization (%)**: Target >80%, measured via tools like `nvidia-smi`.
- **Scalability**: TPS comparison across 3 vs. 5 GPUs (target ~1.6× increase).
- **⏱️ Time Estimate**: ~1.5–2 hours.

---

## 🧪 Test 2: Latency of Single ZKP Computation (Time to First Proof)

**🎯 Objective**: Evaluate the end-to-end latency of generating a single ZKP, emphasizing CPU–GPU handoff efficiency.

### 🛠️ Setup
- Same ZKP protocol as Test 1.
- Use 1× H100 GPU + high-performance CPU (e.g., AMD EPYC or Intel Xeon with TEE).
- Simulate a single confidential transaction.

### ▶️ Execution
- Measure time from transaction input to proof output.
- Repeat 50–100 times for statistical accuracy.

### 📊 Metrics
- **Time to First Proof (TTFP)**: Target 50–200 ms.
- **CPU–GPU Transfer Overhead**: Target <10% of TTFP.
- **Consistency (SD)**: Target <5% deviation.
- **⏱️ Time Estimate**: ~1 hour.

---

## 🧪 Test 3: Performance Impact of TEE for Confidentiality

**🎯 Objective**: Assess the overhead of enabling Trusted Execution Environments (TEE) on H100 GPUs.

### 🛠️ Setup
- Enable TEE (CC-On mode) on 3× H100 GPUs.
- Use the ZKP workload from Test 1.
- Process 5,000 transactions.
- Compare TEE-On vs. TEE-Off modes.

### ▶️ Execution
- Run workload twice: with and without TEE.
- Ensure secure execution with bounce buffers and remote attestation.

### 📊 Metrics
- **TPS Overhead (%)**: Target <7%.
- **Latency Increase (ms)**: Target <5 ms.
- **Memory Bandwidth Utilization**: Target >50% of 3 TB/s HBM3 bandwidth.
- **⏱️ Time Estimate**: ~2–2.5 hours.

---

## 🧪 Test 4: Energy Efficiency of CPU–GPU Collaboration

**🎯 Objective**: Quantify the power efficiency of ZKP acceleration using multiple H100 GPUs.

### 🛠️ Setup
- Use 5× H100 GPUs on Test 1 workload (10,000 transactions).
- Monitor power draw with NVIDIA tools (e.g., NVML API, `nvidia-smi`).
- CPU with TEE support (e.g., AMD EPYC with SEV-SNP).

### ▶️ Execution
- Run workload at peak throughput for 30 minutes.
- Record energy consumption and output.

### 📊 Metrics
- **Transactions per Watt (TPW)**: Target 0.5–1 TPW.
- **Total Power Draw**: Target <4000 W (CPU + 5 GPUs).
- **Efficiency Scaling**: Compare TPW for 3 vs. 5 GPUs.
- **⏱️ Time Estimate**: ~1–1.5 hours.

---

## ⚙️ Practical Considerations

- **⏳ Time Management**: Total time: ~5.5–7 hours. If limited, prioritize **Tests 1 & 3** (throughput + confidentiality).
- **💻 Software**:
  - CUDA 12.4+ for H100 support.
  - Libraries: cuFFT, cuBLAS for math.
  - ZKP frameworks: `libsnark`, `bellman`, etc.
- **🔍 Verification**:
  - Log all metrics, timestamps, and GPU states.
  - Cross-check with theoretical H100 performance (e.g., 130 TPS for medium workloads).
- **🖥️ Hardware Requirements**:
  - Access to 3–5 H100 GPUs (e.g., DGX H100).
  - Compatible CPU with TEE.

---

## ✅ Expected Outcomes

| Test | Expected Result |
|------|-----------------|
| Test 1 | 100–200 TPS with near-linear scaling (reflects Nethermind’s optimization) |
| Test 2 | TTFP < 50 ms (tight CPU–GPU integration) |
| Test 3 | TEE overhead < 5% TPS drop |
| Test 4 | PPW > 0.3 (energy-efficient acceleration) |
