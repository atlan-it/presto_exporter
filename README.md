presto_exporter
==============

Presto exporter for Prometheus. For other metrics from Presto, have a look at the [JMX exporter](https://github.com/prometheus/jmx_exporter) and [Node exporter](https://github.com/prometheus/node_exporter).

Table of Contents
-----------------

-	[Compatibility](#compatibility)
-	[Dependency](#dependency)
-	[Download](#download)
-	[Compile](#compile)
	-	[build binary](#build-binary)
	-	[run binary](#run-binary)
-	[Docker](#docker)
  	-	[run docker](#run-docker)
-	[Flags](#flags)
-	[Metrics](#metrics)
	-	[Topics](#topics)

Compatibility
-------------

Support [Presto](https://prestodb.io/) version 0.177 (and later).

Dependency
----------

-	[Prometheus](https://prometheus.io)
-	[Golang](https://golang.org)
-	[Dep](https://github.com/golang/dep)

Download
--------

Binary can be downloaded from [Releases](https://github.com/yahoojapan/presto_exporter/releases) page.

Compile
-------

### build binary

It can use go to binary by youself

```shell
go build presto_exporter.go
```

### run binary

```shell
./presto_exporter [flags]
```

Docker
-------

### run docker

[![Docker Pulls](https://img.shields.io/docker/pulls/yahoojapan/presto-exporter.svg?maxAge=604800)][hub]

To run the presto exporter as a Docker container, run:

```bash
docker run yahoojapan/presto-exporter:master [flags]
```

[hub]: https://hub.docker.com/r/yahoojapan/presto-exporter/

Flags
-----

This image is configurable using different flags

| Flag name          | Default    | Description                                          |
| ------------------ | ---------- | ---------------------------------------------------- |
| web.listen-address | :9483      | Address to listen on for web interface and telemetry |
| web.telemetry-path | /metrics   | Path under which to expose metrics                   |

Help on flags:

```bash
./presto_exporter --help
```

Metrics
-------

Documents about exposed Prometheus metrics.

For details on the underlying metrics please see [Presto](https://prestodb.io/docs/current/).

### Topics

**Prometheus Metrics Details**

| Name                                               | Exposed informations                                |
| -------------------------------------------------- | --------------------------------------------------- |
| `presto_cluster_running_queries`                           | Total number of queries currently running                 |
| `presto_cluster_active_ workers`                           | Total number of active worker nodes                 |
| `presto_cluster_total_input_rows`                          | Total number of input rows processed                 |
| `presto_cluster_queued_queries`                           | Total number of queries currently queued and awaiting execution                 |
| `presto_cluster_running_drivers`                           | Moving average of total running drivers                   |
| `presto_cluster_total_input_bytes`                         | Total number of input bytes processed                   |
| `presto_cluster_blocked_queries`                           | Total number of queries currently blocked and unable to make progress                 |
| `presto_cluster_reserved_memory`                           | Total amount of memory reserved by all running queries                 |
| `presto_cluster_total_cpu_time_secs`                           | Total number of CPU time                  |


**Metrics output example**

```txt
# HELP presto_cluster_active_workers Active workers of the presto cluster.
# TYPE presto_cluster_active_workers gauge
presto_cluster_active_workers 5
# HELP presto_cluster_blocked_queries Blocked queries of the presto cluster.
# TYPE presto_cluster_blocked_queries gauge
presto_cluster_blocked_queries 0
# HELP presto_cluster_queued_queries Queued queries of the presto cluster.
# TYPE presto_cluster_queued_queries gauge
presto_cluster_queued_queries 0
# HELP presto_cluster_reserved_memory Reserved memory of the presto cluster.
# TYPE presto_cluster_reserved_memory gauge
presto_cluster_reserved_memory 0
# HELP presto_cluster_running_drivers Running drivers of the presto cluster.
# TYPE presto_cluster_running_drivers gauge
presto_cluster_running_drivers 0
# HELP presto_cluster_running_queries Running requests of the presto cluster.
# TYPE presto_cluster_running_queries gauge
presto_cluster_running_queries 0
# HELP presto_cluster_total_cpu_time_secs Total cpu time of the presto cluster.
# TYPE presto_cluster_total_cpu_time_secs gauge
presto_cluster_total_cpu_time_secs 118176
# HELP presto_cluster_total_input_bytes Total input bytes of the presto cluster.
# TYPE presto_cluster_total_input_bytes gauge
presto_cluster_total_input_bytes 7.483291091e+10
# HELP presto_cluster_total_input_rows Total input rows of the presto cluster.
# TYPE presto_cluster_total_input_rows gauge
presto_cluster_total_input_rows 4.085938e+09
# HELP process_cpu_seconds_total Total user and system CPU time spent in seconds.
# TYPE process_cpu_seconds_total counter
```
