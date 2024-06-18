## About this project

Production environment is equipped with Grafana, Prometheus, PostgreSQL, and Node Exporter, forming a robust monitoring stack that provides real-time insights into system metrics and performance across our infrastructure. This setup ensures proactive monitoring, efficient resource management, and reliable performance analysis to support our operational goals effectively.

## Feature
- Node Exporter v1.8.1
- Prometheus v2.52.0
- Postgres
- Grafana

## Installation
1. Run this command to make container can access `grafana` folder
    ```bash
    mkdir -p grafana
    mkdir -p grafana/storage
    sudo chmod -R 777 grafana
    ```

2. Create password for node_exporter with this command
    ```bash
    htpasswd -nBC 10 "" | tr -d ':\n' && echo
    ```

3. Change value inside **config/node_exporter.yml**
    ```yaml
    basic_auth_users:
        prom: <GENERATED FROM HTPASSWD>
    ```
4. Run docker compose
    ```bash
    docker compose --build -d
    ```