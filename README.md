# My Personal System Monitoring Setup

This is a Docker Compose file that sets up a personal system monitoring environment. It includes the following services:

## Services:

- [node_exporter](https://github.com/prometheus/node_exporter?tab=readme-ov-file#node-exporter): Collects system metrics from the host machine.
- [prometheus](https://prometheus.io/docs/prometheus/latest/installation/): Stores and queries metrics from various sources, including node_exporter.
- [grafana](https://grafana.com/docs/grafana/latest/setup-grafana/installation/docker/): Creates customizable dashboards and visualizations for monitoring and analyzing metrics.
- [cadvisor](https://github.com/google/cadvisor): Monitors resource usage and performance metrics of running containers.
## Volumes:
- prometheus_data: Used by Prometheus to store data.
- grafana_data: Used by Grafana to store data.

## Networks:
- monitor: The network used for communication between the services.

Please make sure you have Docker installed and running on your system before using this Docker Compose file. Adjust the file paths and configurations as needed for your environment.

To start the system monitoring setup, navigate to the directory containing this Docker Compose file and run the following command:

```
docker-compose up -d
```

This will create and start the containers for each service defined in the Compose file. You can access the monitoring interfaces by visiting the following URLs:

- Prometheus: [http://localhost:9090](http://localhost:9090)
- Grafana: [http://localhost:3030](http://localhost:3030)
- Cadvisor: [http://localhost:8080](http://localhost:8080)

Feel free to customize the Prometheus and Grafana configurations according to your monitoring needs. Happy monitoring!

## Troubleshooting
### Docker memory usage is always 0
https://github.com/docker/for-linux/issues/1112

https://github.com/stefanprodan/dockprom/issues/228

Fix: append the following to the `\boot\cmdline.txt`: `cgroup_memory=1 cgroup_enable=memory`