# CMUTube Learning Goals

## Checkpoint 1

- Understand the structure of adaptive video streaming:
  - A manifest stores metadata for the video and its available representations.
  - Video is divided into chunks, with corresponding chunks available at different quality levels.
  - An adaptive bitrate (ABR) algorithm selects which representation to request for each chunk based on available signals and network conditions.
- Understand how chunk download time, chunk playback duration, and requested bitrate affect the playback buffer.

- Understand how to implement BBA-0:
  - Use buffer occupancy as signal when choosing the quality of the next chunk.
  - Identify the components of a buffer-to-bitrate curve: x-axis, y-axis, reservoir, cushion, upper reservoir, and quality thresholds.
  - Predict how changing the reservoir, cushion, or thresholds affects bitrate selection and rebuffering risk.
- Be able to trace the quality selected for a series of buffer levels using a given curve and a discrete set of available representations.
- Understand the strengths and weaknesses of buffer-based algorithms (e.g., conservative startup even when bandwidth is high).
- Explain why a continuously increasing target bitrate may still produce discrete quality changes.

### QoE metrics and network workloads

- Understand the project's QoE metrics: time-to-first-frame (TTFF), average bitrate, quality switches, rebuffer count, and stall time.
- Explain how applications weight metrics differently (e.g., TTFF is especially important for short-form video).
- Calculate and compare composite QoE scores given individual metric values and weights.
- Evaluate tradeoffs: determine when optimizing for one metric offsets degradation in another.
- Reason about how steady, oscillating, abruptly changing, high-jitter, and real-world network traces affect QoE.
- Identify why an algorithm performs well for certain workloads, but not others.
- Predict which network changes are likely to trigger rebuffering, quality oscillation, or underutilization of available bandwidth.

### Evaluation

- Explain the strengths and limitations of buffer occupancy, measured throughput, and latency as ABR signals.
- Reason about how certain measurements affect bitrate decisions (e.g. high jitter, oscillating, etc).
- Discuss how introducing latency and throughput signals can improve or worsen a buffer-based algorithm's QoE.
- Conduct an ablation study that isolates the contributions of individual signals.
## Checkpoint 2

### Application-aware algorithm design

- Identify mechanisms that can improve particular QoE metric.
- Reason about tradeoffs between optimizing one metric and degrading another.
- Propose and justify ABR modifications for a particular application based on how its QoE function weights different metrics.
- Predict how more aggressive or conservative bitrate increases and decreases affect average quality, stalls, TTFF, and quality switches.
- Identify workloads for which an application-specific optimization may help, and workloads or applications for which it may hurt.

### Comparing Checkpoint 1 and Checkpoint 2
- Compare CP1 and CP2 submissions to identify which algorithmic changes were most important for particular applications and QoE metrics.
- Identify which workloads benefited from CP2 change and why.
- Propose a single algorithm that balances the QoE objectives from both checkpoints.


## Do not implement by name
- BBA-0
- BOLA
