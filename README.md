## Hypothesis 2: The OpenTelemetry Collector cannot read from the Docker API because the `/var/run/docker.sock` file is not mounted inside the container.
- **Fix:**
  - [Edited docker compose files (core, minimal, testing)](https://github.com/nmrepos/INFO8985Task1/commit/91b79c35c374a1d44f3a7dfbc356583dd54b3bfd)
    
  - ![image](https://github.com/user-attachments/assets/fb4034b7-9b65-4376-8f8a-a4104d4baea3)
  - Mounted Docker socket to `otel-collector`:
    ```yaml
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    ```
- **Result:** Docker metrics appeared successfully in the SigNoz dashboard.
  
![image](https://github.com/user-attachments/assets/e97f03cd-534e-470d-8a17-802f9ca0cd95)

