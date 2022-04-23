# Ansible Role: InfluxDB v2 Task

Ansible role creating/updating [tasks](https://docs.influxdata.com/influxdb/cloud/process-data/manage-tasks/create-task/) in InfluxDB v2.

## Required Input Variables

```yaml
influxdb_v2_task_url: http://localhost:8086
influxdb_v2_task_url_username: admin
influxdb_v2_task_url_password: admin-password
influxdb_v2_task_org: someorg
influxdb_v2_task_name: sometask
influxdb_v2_task_every: 5m
influxdb_v2_task_flux: |
  from(bucket: "source")
      |> filter(fn: (r) => r["_field"] == "somefield")
      |> to(host: "http://localhost:8086", org: "otherorg", token: "secret", bucket: "targetbucket")
```

## Optional Input Variables

```yaml
influxdb_v2_task_flux_imports: [regexp, strings]
```

## Rationale

Ansible's `influxdb_*` modules do not support InfluxDB v2 as they are based on https://github.com/influxdata/influxdb-python:

> Note: This library is for use with InfluxDB 1.x. For connecting to InfluxDB 2.x instances, please use the the influxdb-client-python client.
