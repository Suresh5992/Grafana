
                    ** Grafana Monitoring Setup Summary**


**✅ Server Roles**

---------------------------------------------------------------
| Component          | Server Type                           |
---------------------------------------------------------------
| Prometheus         | Master (Installed)                    |
| Promtail           | Master (Installed)                    |
| Alertmanager       | Master (Installed)                    |
| Loki               | Master (Installed)                    |
| Node Exporter      | Agent (Target Servers)                |
| Windows Exporter   | Agent (Target Servers)                |
| Blackbox Exporter  | Agent (Target Servers)                |
---------------------------------------------------------------

 
**✅ Application & Infrastructure Monitoring**
 

---------------------------------------------------------------------------
| Component          | Description               | Port  | Configuration   |
---------------------------------------------------------------------------
| Node Exporter      | Linux Server Monitoring   | 9100  | YAML in Prometheus |
| Windows Exporter   | Windows Server Monitoring | 9182  | YAML in Prometheus |
| Blackbox Exporter  | Port, HTTP, TCP Monitoring| 9115  | YAML in Prometheus |
---------------------------------------------------------------------------


**✅ Port & Protocol Monitoring**


---------------------------------------------------------------------------
| Component          | Description                                      |
---------------------------------------------------------------------------
| Blackbox Exporter  | Linux & Windows agent – monitors HTTP, HTTPS, TCP |
---------------------------------------------------------------------------
✔️ Configuration Path: `/etc/prometheus/prometheus.yml`
✔️ Blackbox Exporter: Must be installed on production/target servers.
✔️ Prometheus: Add IP and Port in YAML for port monitoring.


**✅ Logs Monitoring (Live Transactions)**


---------------------------------------------------------------
| Component  | Role                 | Flow                    |
---------------------------------------------------------------
| Promtail   | Agent (Log Collector) | Push logs to Loki       |
| Loki       | Storage               | Stores application logs |
| Grafana    | Dashboard             | Visualize logs (Live)   |
---------------------------------------------------------------

✔️ Push Mechanism: Promtail pushes logs directly to Loki.  
✔️ Query Language: LogQL  
✔️ Dashboard: Custom dashboards required for live log monitoring.  
✔️ Datasource: Loki  

 
**✅ Full Monitoring Stack Overview**
 

---------------------------------------------------------------------------
| Feature                | Source Component   | Collection Type | Visualized In |
---------------------------------------------------------------------------
| Linux Infra Metrics    | Node Exporter      | Pull            | Grafana       |
| Windows Infra Metrics  | Windows Exporter   | Pull            | Grafana       |
| Ports & Protocols      | Blackbox Exporter  | Pull            | Grafana       |
| Application Logs       | Promtail           | Push            | Grafana       |
---------------------------------------------------------------------------

 
**✅ Push vs Pull Summary**
 

---------------------------------------------------------------
| Method | Components                | Notes                  |
---------------------------------------------------------------
| Push   | Promtail                  | Pushes logs to Loki    |
| Pull   | Node Exporter (Linux)     | Prometheus pulls metrics |
|        | Windows Exporter          | Prometheus pulls metrics |
|        | Blackbox Exporter         | Prometheus pulls port/HTTP/TCP metrics |
---------------------------------------------------------------

 
**✅ Key Notes**
 

✔️ Prometheus: Pulls all infra and port metrics (Configured in prometheus.yml)  
✔️ Promtail: Pushes application logs to Loki  
✔️ Blackbox Exporter: Used for port, HTTP, HTTPS, TCP checks  
✔️ Grafana: Dashboards for logs, infra metrics, and port status  
✔️ Grafana Templates: Available in Grafana Labs for quick setup

 
**✅ Quick Configuration Paths**
 

✔️ Prometheus YAML Path: `/etc/prometheus/prometheus.yml`  
✔️ Grafana Dashboards: Use templates from Grafana Labs + Create custom dashboards for logs


