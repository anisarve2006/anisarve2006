<div align="center">

<table border="0" style="border: none;">
  <tr style="border: none;">
    <td width="78%" align="left" style="border: none; padding-left: 20px;">
      <h1>Anirudh Sarve</h1>
      <p><strong>Systems Software Engineer | Edge AI & Computer Vision | Distributed Systems</strong></p>
      <p>Computer Engineering Undergraduate at Vidyalankar Institute of Technology, Mumbai (CGPA: 8.90 / 10.0)</p>
      <p>
        <a href="https://anirudh-sarve.me"><img src="https://img.shields.io/badge/Portfolio-anirudh--sarve.me-059669?style=flat-square&logo=google-chrome&logoColor=white" alt="Portfolio" /></a>
        <a href="https://www.linkedin.com/in/anirudh-sarve-2130a724a"><img src="https://img.shields.io/badge/LinkedIn-Profile-0077B5?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
        <a href="mailto:anisarve2006@gmail.com"><img src="https://img.shields.io/badge/Email-anisarve2006%40gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white" alt="Email" /></a>
      </p>
    </td>
  </tr>
</table>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=15&duration=3000&pause=1000&color=059669&center=true&vCenter=true&width=620&lines=Computer+Engineering+Undergraduate+%7C+VIT+Mumbai;Lead+AI+Architect+%7C+ISRO+Problem+Statement+26168;Real-Time+State+Estimation+%26+15-State+ESKF+in+C%2B%2B;Low-Latency+Inference+Runtimes+%26+Distributed+Systems" alt="Typing Banner" />
</p>

</div>

---

### Technical Specialization

- **State Estimation & Sensor Fusion:** Real-time inertial navigation algorithms coupling high-rate IMU mechanization with a 15-state Error-State Kalman Filter (ESKF) running on embedded ARM platforms under total GNSS signal outages.
- **Computer Vision & Generative AI:** Cross-modal optical and Synthetic Aperture Radar (SAR) translation networks with custom differentiable Spectral Angle Mapper (SAM) loss, reaching 32.09 dB PSNR on satellite imagery.
- **Systems & Low-Latency Runtimes:** In-browser client-side neural inference via WebAssembly and WebGL (<3.5s latency, zero recurring server GPU egress cost), atomic distributed locks in Upstash Redis, and user-space TCP/IP protocol stacks.

---

### Engineering Toolkit

| Domain | Frameworks, Languages, and Infrastructure |
| :--- | :--- |
| **Languages** | C++ (C++17/20), Python, TypeScript, JavaScript (Node.js), SQL, Go, Rust (Foundations) |
| **Systems & Cloud** | Linux/POSIX, WebAssembly (WASM), WebGL, Docker, WebSockets, gRPC, Microservices, CI/CD, AWS, GCP |
| **AI, Perception & Runtimes** | PyTorch, ONNX Runtime, CUDA / TensorRT, OpenCV, 15-State ESKF, Sensor Fusion, ResU-Net, Scikit-learn |
| **Data & Storage** | PostgreSQL, Upstash Redis (Atomic Distributed Locks), MongoDB (2dsphere), Qdrant Vector DB, SQLite FTS5 |

---

### Key Engineering Systems & Architecture

#### 1. Neural-Inertial Dead-Reckoning Engine with 15-State ESKF
**Repository:** [github.com/anisarve2006/Dead-Reckoning-Model](https://github.com/anisarve2006/Dead-Reckoning-Model)  
**Affiliation:** Lead AI Architect, Smart India Hackathon (ISRO Problem Statement 26168)  
**Technologies:** C++17, PyTorch, 15-State ESKF, IMU Mechanization, ARM Cortex-A

Real-time odometry and vehicular dead-reckoning navigation architecture designed to sustain localization accuracy during complete GNSS/GPS blackouts. Executes raw 10 Hz IMU kinematic integration coupled with zero-velocity updates (ZUPT) and non-holonomic velocity constraints in C++ at sub-3.0 ms CPU execution latency per cycle on embedded ECUs.

<!-- <div align="center">
  <img src="assets/eskf_inertial.jpg" alt="15-State ESKF Architecture" width="850" style="border-radius: 8px; border: 1px solid #cbd5e1;" />
</div> -->

```mermaid
flowchart LR
    A["Raw 10Hz IMU<br/>(Acc / Gyro)"] --> B["Nominal State<br/>Mechanization"]
    B --> C["15-State Error-State<br/>Kalman Filter (C++)"]
    D["Kinematic Constraints<br/>(ZUPT & Non-Holonomic)"] --> C
    C --> E["Corrected 3D State<br/>(Position, Velocity, Attitude)"]
    E --> F["Zero-Latency State Reset<br/>& Covariance Update"]
```

---

#### 2. Multimodal Optical-SAR Satellite Cloud Removal ResU-Net
**Repository:** [github.com/anisarve2006/Temporal-Cloud-Removal](https://github.com/anisarve2006/Temporal-Cloud-Removal)  
**Application:** ISRO Resourcesat-2/2A LISS-IV & Sentinel-1 C-Band Radar Fusion  
**Technologies:** PyTorch, ResU-Net, Cross-Modal Attention, Sentinel-1 SAR C-Band

Deep generative reconstruction network bridging radar backscatter and high-resolution (5.0 m) optical spectral bands over persistently cloud-covered terrain. Engineered with a custom differentiable Spectral Angle Mapper (SAM) loss function, achieving **32.09 dB PSNR**, **0.7167 SSIM**, and a strict **6.17 deg SAM spectral angle** on validation scenes across the Assam river corridor.

<!-- <div align="center">
  <img src="assets/optical_sar.jpg" alt="Multimodal Optical-SAR Fusion Architecture" width="850" style="border-radius: 8px; border: 1px solid #cbd5e1;" />
</div> -->

```mermaid
flowchart LR
    S["Sentinel-1 SAR C-Band<br/>(VV/VH Polarization)"] --> R["Radar Feature Encoder<br/>(Noise Despeckling)"]
    L["LISS-IV Optical Bands<br/>(Cloud-Occluded)"] --> O["Optical Feature Encoder<br/>(Spectral Extraction)"]
    R --> M["Cross-Modal Attention<br/>Fusion Bottleneck"]
    O --> M
    M --> D["ResU-Net Decoder &<br/>Skip Connections"]
    D --> SAM["Differentiable SAM Loss<br/>+ L1 Reconstruction"]
    SAM --> OUT["Reconstructed 5.0m<br/>Cloud-Free Optical Image"]
```

---

#### 3. ProtoLink: Custom User-Space TCP/IP Protocol Stack & Dissector
**Repository:** [github.com/anisarve2006/custom-tcp-ip-stack](https://github.com/anisarve2006/custom-tcp-ip-stack)  
**Technologies:** C++, Systems Programming, Raw Sockets, Network Protocols, State Machines

From-scratch implementation of core Internet protocol suite layers in user space. Manages Ethernet frame encapsulation, ARP resolution tables, IPv4 fragmentation and reassembly, ICMP error handlers, and sliding-window TCP transmission state machines with custom packet inspection and transmission visualization.

<!-- <div align="center">
  <img src="assets/protolink.jpg" alt="ProtoLink Network Protocol Stack" width="850" style="border-radius: 8px; border: 1px solid #cbd5e1;" />
</div> -->

---

#### 4. NAViGO: Autonomous Mobile Robot Perception & Visual SLAM System
**Repository:** [github.com/anisarve2006/Dead-Reckoning-Model](https://github.com/anisarve2006/Dead-Reckoning-Model)  
**Technologies:** C++, ROS 2, OpenCV, Point Cloud Processing, Embedded Computing

Perception and local navigation stack for autonomous rovers operating across unstructured environments. Integrates real-time feature extraction, visual odometry, local costmap generation, and obstacle avoidance pathways calculated via dynamic window trajectory evaluation.

<!-- <div align="center">
  <img src="assets/navigo.jpg" alt="NAViGO Autonomous Navigation Architecture" width="850" style="border-radius: 8px; border: 1px solid #cbd5e1;" />
</div> -->

---

#### 5. StandIQ: Autonomous Indian Standards Intelligence & Compliance Engine
**Repository:** [github.com/anisarve2006/StandIQ](https://github.com/anisarve2006/StandIQ)  
**Affiliation:** Smart India Hackathon (SIH 2026 Problem Statement 108)  
**Technologies:** FastAPI, SQLite FTS5, ONNX Runtime, PaddleOCR, Reciprocal Rank Fusion

Neuro-symbolic compliance search engine built to parse, index, and cross-reference tender requirements against 19,423 Bureau of Indian Standards (BIS) regulatory documents. Combines BM25 lexical ranking, regex token filters, and dense vector embeddings via Reciprocal Rank Fusion, integrated with OCR extraction maintaining 99.28% recognition accuracy on multi-column tender schedules.

<!-- <div align="center">
  <img src="assets/vericlaim.jpg" alt="StandIQ Compliance Intelligence Engine" width="850" style="border-radius: 8px; border: 1px solid #cbd5e1;" />
</div> -->

---

#### 6. Client-Side Edge Neural Vision Runtime & In-Browser Matting Engine
**Technologies:** WebAssembly (WASM), WebGL, U²-Net, ONNX Runtime Web, TypeScript

Zero-backend client-side computer vision runtime processing high-precision photo-matting and human segmentation directly inside the user's browser in sub-3.5 seconds. Eliminates external cloud GPU inference latency and recurring egress costs through WebGL hardware acceleration.

<!-- <div align="center">
  <img src="assets/virtual_tryon.jpg" alt="Client-Side Edge Neural Vision Runtime" width="850" style="border-radius: 8px; border: 1px solid #cbd5e1;" />
</div> -->


### GitHub Activity and Contribution Metrics

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=anisarve2006&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=059669&icon_color=059669&text_color=94a3b8" height="150" alt="GitHub Stats" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=anisarve2006&layout=compact&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=059669&text_color=94a3b8" height="150" alt="Top Languages" />
</div>

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=anisarve2006&theme=tokyonight&hide_border=true&background=0d1117&ring=059669&fire=059669&currStreakLabel=059669" alt="GitHub Streak" />
</p>

---

<div align="center">
  <strong>Contact and Professional Links:</strong> 
  <a href="https://anirudh-sarve.me">Portfolio</a> | 
  <a href="https://www.linkedin.com/in/anirudh-sarve-2130a724a">LinkedIn</a> | 
  <a href="mailto:anisarve2006@gmail.com">Email</a>
</div>
