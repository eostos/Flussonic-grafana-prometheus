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
# How to Add JSON Configuration to a Grafana Dashboard

This guide will walk you through the process of importing or adding a JSON configuration to your Grafana dashboard.

## Prerequisites

- Make sure you have administrative or edit permissions for the Grafana instance where you want to add the dashboard.
- Ensure you have the JSON configuration ready that you want to import into Grafana.

## Instructions

### Step 1: Accessing Grafana

1. Open your web browser.
2. Enter the URL of your Grafana instance and log in with your credentials.

### Step 2: Importing Dashboard JSON

1. Once logged in, click on the **"+"** (plus) icon on the left-hand side navigation menu.
2. Select **"Import"** from the options that appear.

### Step 3: Adding the JSON

1. In the import interface, you will see an area where you can paste the JSON code.
2. Copy your JSON dashboard configuration.
3. Paste the JSON code into the text area provided.

### Step 4: Setting Up the Dashboard

1. After pasting the JSON, you may need to select the correct data source from a dropdown if the JSON contains any datasource-specific queries.
2. You may also need to adjust any variables or settings that are specific to your environment or that were not defined in the JSON.

### Step 5: Finalizing the Import

1. Click on the **"Load"** button to preview the dashboard.
2. Review the dashboard to ensure that everything is configured correctly.
3. If everything looks good, click on the **"Import"** button to add the dashboard to your Grafana instance.

## Conclusion

You have successfully added a new dashboard to Grafana using a JSON configuration. You can now view and interact with your data on the new dashboard.

## Troubleshooting

If you encounter any errors:
- Verify that the JSON format is correct and valid.
- Check if all required fields are filled out, especially the `uid` and `id` fields.
- Make sure the data sources in the JSON configuration are available in your Grafana instance.

Remember that dashboard JSON structures may change between Grafana versions, so ensure your JSON is compatible with your Grafana version.
