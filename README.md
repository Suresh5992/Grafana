# Grafana

#Logging, Infrastructure, and Port Monitoring

✅ Server Roles

| Component         | Server Type            |
| ----------------- | ---------------------- |
| Prometheus        | Master (Installed)     |
| Promtail          | Master (Installed)     |
| Alertmanager      | Master (Installed)     |
| Loki              | Master (Installed)     |
| Node Exporter     | Agent (Target Servers) |
| Windows Exporter  | Agent (Target Servers) |
| Blackbox Exporter | Agent (Target Servers) |

✅ Application & Infra Monitoring

| Component         | Description                | Port | Configuration             |
| ----------------- | -------------------------- | ---- | ------------------------- |
| Node Exporter     | Linux Server Monitoring    | 9100 | YAML target in Prometheus |
| Windows Exporter  | Windows Server Monitoring  | 9182 | YAML target in Prometheus |
| Blackbox Exporter | Port, HTTP, TCP Monitoring | 9115 | YAML target in Prometheus |

Prometheus: Master server – Pulls metrics from agents

PromQL: Query language used by Prometheus

Grafana Dashboards: Templates available in Grafana Labs

✅ Port & Protocol Monitoring

| Component          | Description                                              |
| ------------------ | -------------------------------------------------------- |
| Blackbox Exporter  | Linux & Windows agent – monitors HTTP, HTTPS, TCP, Ports |
| Configuration Path | `/etc/prometheus/prometheus.yml`                         |

Blackbox Exporter: Must be installed on production/target servers.
Prometheus Configuration: Add IP and port in YAML to monitor.

✅ Logs Monitoring (Live Transactions)

| Component | Role                  | Flow                    |
| --------- | --------------------- | ----------------------- |
| Promtail  | Agent (Log Collector) | Push logs to Loki       |
| Loki      | Storage               | Stores application logs |
| Grafana   | Dashboard             | Visualize logs (Live)   |

Push Mechanism: Promtail pushes logs directly to Loki.

Query Language: LogQL
Dashboard: Must create custom dashboards for application live log monitoring.
Datasource: Loki

✅ Full Monitoring Stack Overview

| Feature               | Source Component  | Collection Type | Visualization |
| --------------------- | ----------------- | --------------- | ------------- |
| Linux Infra Metrics   | Node Exporter     | Pull            | Grafana       |
| Windows Infra Metrics | Windows Exporter  | Pull            | Grafana       |
| Ports & Protocols     | Blackbox Exporter | Pull            | Grafana       |
| Application Logs      | Promtail          | Push            | Grafana       |

✅ Key Notes
Prometheus: Pulls all infra and port metrics (configured via prometheus.yml).
Promtail: Pushes application logs to Loki.
Blackbox Exporter: Use for Port, HTTP, HTTPS, TCP checks (Linux & Windows).
Grafana: Dashboards to visualize logs, infra metrics, and port status.
Templates: Available in Grafana Labs for quick setup.

✅ #Quick Configuration Paths
Prometheus Config: /etc/prometheus/prometheus.yml
Dashboards: Grafana Labs templates (also create custom ones for application logs)


