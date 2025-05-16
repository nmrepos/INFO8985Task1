**Hypothesis:** The OpenTelemetry Collector is not collecting container metrics because the `docker_stats` receiver is missing.
- **Fix:**
  - Added `docker_stats` receiver in `otel-collector-config.yaml`
  - Modified `metrics` pipeline to include the receiver
- **Result:** Metrics still did not show up — socket access missing.
