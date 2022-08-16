# Ansible Role: InfluxDB v2 Organization

Ansible role creating [organizations](https://docs.influxdata.com/influxdb/cloud/organizations/view-orgs/) in InfluxDB v2.

## Required Input Variables

```yaml
influxdb_v2_organization_url: http://localhost:8086
influxdb_v2_organization_url_username: admin
influxdb_v2_organization_url_password: admin-password
influxdb_v2_organization_name: sometask
```

## Optional Input Variables

```yaml
influxdb_v2_organization_buckets_create: # does not overwrite; default: [] (no new buckets)
- {name: abcdef, retention_rules: []}
- {name: ghijkl, retention_rules: []}
influxdb_v2_organization_fetch_buckets: true # default: false
influxdb_v2_organization_fetch_members: true # default: false
influxdb_v2_organization_fetch_owners: true # default: false
```

## Output Variables

```
influxdb_v2_organization_id
influxdb_v2_organization_buckets # when influxdb_v2_organization_fetch_buckets true
influxdb_v2_organization_members # when influxdb_v2_organization_fetch_members true
influxdb_v2_organization_owners # when influxdb_v2_organization_fetch_owners true
influxdb_v2_organization_url_cookies_string
```

## Rationale

Ansible's `influxdb_*` modules do not support InfluxDB v2 as they are based on https://github.com/influxdata/influxdb-python:

> Note: This library is for use with InfluxDB 1.x. For connecting to InfluxDB 2.x instances, please use the the influxdb-client-python client.
