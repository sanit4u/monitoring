# monitoring
This gives an idea about installing prometheus and monitoring with Grafana in windows as a standalone system.
Prometheus is a pull based monitoring system, which pulls the monitoring statistics from the agent exporters and saves it in it's timeseries database. 
Prometheus comes with a simple graph ui for simple graph visualiyation. However, to visualize the metrics in a dashboard, Grafana can be used.

## Installation of Prometheus in windows
- The setup consists of prometheus server and the windows node exporter in a single host.

### versions
 - [Prometheus](https://prometheus.io/download/) version: 2.15.2.(choose the operating system and architecture from the drop down.)
 - Windows 10
 - [Windows Node exporter](https://github.com/martinlindhe/wmi_exporter/releases) version: 0.9.0-amd64 

### steps
 - Download the prometheus tar.gz file 
 - Unzip the tar.gz file
 - Download the Windows Node exporter (wmi) msi file.
 - start the wmi execuatable.
 - by default it start the exporter in 9182 port.
 - In the prometheus folder, open the prometheus.yml, change the target port to 9182. so that the prometheus can pull the metrics from the  wmi agent.
  
  ```
    scrape_configs:
      # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
      - job_name: 'prometheus'
        static_configs:
           - targets: ['localhost:9182']
 ```
 - start the promehteus by executing the prometheus.exe 
 
 ### Testing the setup
 - By default, prometheus server can be accessed using 9090 port.
