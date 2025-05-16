**Hypothesis 2:** The OpenTelemetry Collector cannot read from the Docker API because the `/var/run/docker.sock` file is not mounted inside the container.
- **Fix:**
  - Edited `docker-compose-minimal.yaml`
  - Mounted Docker socket to `otel-collector`:
    ```yaml
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    ```
- **Result:** Docker metrics appeared successfully in the SigNoz dashboard.
- ![image](https://github.com/user-attachments/assets/ab831559-ce7f-495f-93bc-09b6713787f3)
