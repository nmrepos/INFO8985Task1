# Class Activity 1 - Submission

## Problem Statement

Signoz has a facility to monitor docker. Unfortunately in https://github.com/rhildred/signoz it doesn't seem to work. Generate at least 2 ideas about what the issue is, looking on the internet and especially at the otel collector config, and the versions of software in the docker compose.
---
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

---

### 2 [`fix-docker-socket`](https://github.com/nmrepos/INFO8985Task1/tree/fix-docker-socket)

- **Hypothesis 2:** The OpenTelemetry Collector cannot read from the Docker API because the `/var/run/docker.sock` file is not mounted inside the container.
- **Fix:**
  - Edited docker compose files (core, minimal, testing)
  - ![image](https://github.com/user-attachments/assets/fb4034b7-9b65-4376-8f8a-a4104d4baea3)
  - Mounted Docker socket to `otel-collector`:
    ```yaml
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    ```
- **Result:** Docker metrics appeared successfully in the SigNoz dashboard.
- **Conclusion:** This fix resolved the issue — the collector now has access to container stats.
---

## 📷 Result Screenshot
services
![image](https://github.com/user-attachments/assets/35251e44-d34d-447e-ae92-fb5493e73be3)
---
frontend
![image](https://github.com/user-attachments/assets/0012298c-12d5-407f-9567-79c7b70f5e30)
---
redis
![image](https://github.com/user-attachments/assets/543899d4-09e9-473a-9983-a0b1ef097d7b)
---
mysql
![image](https://github.com/user-attachments/assets/69a5aef2-5300-48fd-907a-e8b70f890211)
---
/customer endpoint (GET)
![image](https://github.com/user-attachments/assets/c4167d16-2676-4c1f-9561-2aceb09f45ce)
---
/route endpoint 
![image](https://github.com/user-attachments/assets/9426b6ba-3349-4d8c-aaae-20a328d5c08f)






