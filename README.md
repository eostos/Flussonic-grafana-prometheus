# Flussonic-grafana-prometheus
Grafana dashboard using Prometheus as a data ingestion with new Flussonic API "/flussonic/api/v3/streams"

## Version
Grafana    10.01 
prometheus 2.47
Flussonic 23.10.1
## Prometheus Configuration
global:
  scrape_interval: 15s
  scrape_timeout: 10s
  evaluation_interval: 15s
alerting:
  alertmanagers:
  - follow_redirects: true
    enable_http2: true
    scheme: http
    timeout: 10s
    api_version: v2
    static_configs:
    - targets:
      - localhost:9093
scrape_configs:
- job_name: SERVER-NAME
  honor_timestamps: true
  scrape_interval: 15s
  scrape_timeout: 10s
  metrics_path: /flussonic/api/v3/streams
  scheme: http
  basic_auth:
    username: admin
    password: <secret>
  follow_redirects: true
  enable_http2: true
  static_configs:
  - targets:
    - SERVERIP
