# Ansible Role: InfluxDB v2 Organization

Ansible role creating [organizations](https://docs.influxdata.com/influxdb/cloud/organizations/view-orgs/) in InfluxDB v2.

## Required Input Variables

```yaml
influxdb_v2_organization_url: http://localhost:8086
influxdb_v2_organization_url_username: admin
influxdb_v2_organization_url_password: admin-password
influxdb_v2_organization_name: sometask
```

## Rationale

Ansible's `influxdb_*` modules do not support InfluxDB v2 as they are based on https://github.com/influxdata/influxdb-python:

> Note: This library is for use with InfluxDB 1.x. For connecting to InfluxDB 2.x instances, please use the the influxdb-client-python client.
