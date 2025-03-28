# zk-SNARK Performance Visualization Guide

## Overview
This guide outlines how to visualize the performance of zk-SNARK proof generation across multiple GPU and TEE configurations. The goal is to support claims related to **optimization**, **collaboration**, and **confidentiality** using intuitive, impactful charts.

---

## 📊 Test 1: Bar Chart – Throughput Across GPU Configurations

**🎯 Purpose**: Show the scalability and throughput of zk-SNARK proof generation.

**Chart Details**:
- **X-Axis**: Number of GPUs (3, 4, 5)
- **Y-Axis**: Proofs per Second (PPS)
- **Bars**: One set per batch size (e.g., 100, 500, 1000 proofs)
- **Annotations**: GPU utilization % (e.g., >85%) above each bar

**💡 Why It Works**:
- Demonstrates scalability (e.g., 1.6× PPS from 3 to 5 GPUs)
- Highlights trade-offs with different batch sizes

**🖼️ Example Caption**:
> Throughput (PPS) of zk-SNARK proof generation with varying GPU counts and batch sizes, showcasing near-linear scalability (e.g., 1.6× PPS from 3 to 5 GPUs).

---

## 📈 Test 2: Line Graph – Latency Breakdown of a Single Proof

**🎯 Purpose**: Illustrate end-to-end latency and CPU–GPU handoff efficiency.

**Chart Details**:
- **X-Axis**: Proof generation stages (e.g., CPU Witness Prep, Data Transfer, GPU Computation)
- **Y-Axis**: Time (ms)
- **Lines**: Avg. time to final proof (TTFP, e.g., 20–100 ms), with error bars (e.g., <5% SD)
- **Highlight**: Shade data transfer time (e.g., <5 ms)

**💡 Why It Works**:
- Breaks down latency contributions to validate system efficiency
- Useful for audiences focused on real-time performance

**🖼️ Example Caption**:
> Latency breakdown of a single zk-SNARK proof, showing efficient CPU–GPU collaboration with minimal transfer overhead (<5 ms).

---

## 🧱 Test 3: Stacked Bar Chart – TEE vs. Non-TEE Performance

**🎯 Purpose**: Compare throughput and latency with and without Trusted Execution Environments (TEE).

**Chart Details**:
- **X-Axis**: Configurations (TEE-Off, TEE-On)
- **Y-Axis**: PPS (primary); Latency (ms) as a secondary axis
- **Stacks**: PPS split into computation vs. overhead
- **Overlay**: Line for latency
- **Annotations**: Overhead % (e.g., <5–7% PPS drop)

**💡 Why It Works**:
- Quantifies trade-offs between confidentiality and performance
- Combines both throughput and latency in one figure

**🖼️ Example Caption**:
> Performance impact of TEE on zk-SNARK proofs, with <5% PPS reduction and <3 ms latency increase, ensuring confidentiality with minimal cost.

---

## 🔵 Test 4: Scatter Plot – Energy Efficiency vs. Throughput

**🎯 Purpose**: Highlight power–performance trade-offs in zk-SNARK generation.

**Chart Details**:
- **X-Axis**: Power Draw (Watts)
- **Y-Axis**: Proofs per Second (PPS)
- **Points**: One per GPU count (3, 4, 5); size = Proofs per Watt (PPW)
- **Trend Line**: Optional to show scaling

**💡 Why It Works**:
- Frames performance in terms of sustainability
- Relevant for large-scale or green deployments

**🖼️ Example Caption**:
> Energy efficiency of zk-SNARK acceleration, achieving >0.3 PPW across 3–5 H100 GPUs with stable scaling.

---

## 🔥 Optional: Heatmap – GPU Utilization Across Workload

**🎯 Purpose**: Visualize how work is distributed across multiple GPUs.

**Chart Details**:
- **X-Axis**: Time (minutes) or Batch #
- **Y-Axis**: GPU ID (1–5)
- **Color Scale**: Utilization % (e.g., green >85%, red <50%)

**💡 Why It Works**:
- Validates load balancing in parallel workloads
- Adds insight into resource scheduling

**🖼️ Example Caption**:
> GPU utilization heatmap during zk-SNARK proof generation, showing consistent >85% usage across 5 H100 GPUs.

---

## 🧠 Publication Strategy

**Core Figures**:
- **Required**: 
  - Test 1 – Throughput (Scalability)
  - Test 2 – Latency (Optimization)
  - Test 3 – TEE Impact (Confidentiality)
  
**Optional**:
- **Test 4 – Energy Efficiency**: Include if space permits
- **Heatmap**: Use only if parallelization is a key claim

---

## 🎨 Style Tips
- Use **consistent color schemes** (e.g., blue = GPU, orange = CPU)
- Use **log scales** when data spans multiple orders of magnitude
- Ensure all axes are **clearly labeled** (PPS, ms, W)
- Keep **legends** clean and accessible

---

## 🔄 Narrative Flow
1. **Start strong** with throughput (Test 1) to establish performance
2. **Add detail** with latency breakdown (Test 2)
3. **Establish trust** with TEE performance (Test 3)
4. **End with impact** via energy efficiency or parallelization (Test 4 or Heatmap)
