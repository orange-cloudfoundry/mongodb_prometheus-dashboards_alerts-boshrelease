#  <p style="text-align:center">MongoDB dashboards & alerts for prometheus-boshrelease</p>
> > ** THIS RELEASE IS STILL UNDER CONSTRUCTION
----------

## Introduction
This release is used as an extension of prometheus deployment.
It adds missing [grafana dashboard](https://grafana.com/dashboards/2583) et prometheus alerts.

## Usage
To deploy the grafana dashboard, edit your prometheus deployment file:

```
releases:
...
  - {name: mongodb_prometheus-dashboards_alerts, version: latest }

instance_groups:
- name: prometheus-server
...
  jobs:
  ...
  - name: mongodb_alerts
    release: mongodb_prometheus-dashboards_alerts
  - name: prometheus
    release: prometheus
    properties:
      prometheus:
	...
        rule_files:
	...
          - /var/vcap/jobs/mongodb_alerts/*.alerts


- name: grafana
...
  jobs:
  ...
  - name: mongodb_dashboards
    release: mongodb_prometheus-dashboards_alerts

```
