## Hypothesis

### 1 [`fix-otel-config`](https://github.com/nmrepos/INFO8985Task1/tree/fix-otel-config/)

- **Hypothesis 1:** The OpenTelemetry Collector is not collecting container metrics because the `docker_stats` receiver is missing.
- **Fix:**
  - Added `docker_stats` receiver in `otel-collector-config.yaml`
  - ![image](https://github.com/user-attachments/assets/2e07e234-5c01-4259-92e8-ea0ec9417bfb)
  - Modified `metrics` pipeline to include the receiver
  - ![image](https://github.com/user-attachments/assets/8851815d-b4a1-4031-924a-5b23a79c021d)
- **Result:** Metrics still did not show up — socket access missing.
- **Conclusion:** This receiver is necessary but **not sufficient alone**.
