# Postfix Monitoring Scripts


This Ansible role automates the deployment of Postfix monitoring scripts for Zabbix, based on the original source code from [rafael747/zabbix-postfix](https://github.com/rafael747/zabbix-postfix).
The role installs all the usual tasks and selects settings depending on the supported distribution, Debian or RedHat.

Also contains a [template for Zabbix](zabbix-template/zbx_postfix_template.7.0.yaml)

## Zabbix Macros
- `{$POSTIX_MAIL_QUEUE_LIMIT}`: Maximum email queue size threshold. Default: `1000`
- `{$POSTFIX_MAIL_QUEUE_TIME_PERIOD}`: Time window during which queue size is not considered critical. Default: `1h`

Alert triggers require both conditions:  
1. Email queue exceeds `{$POSTIX_MAIL_QUEUE_LIMIT}`  
2. Condition persists beyond `{$POSTFIX_MAIL_QUEUE_TIME_PERIOD}`


## Other solutions

If you use Grafana Loki, there are alternative ways to evaluate the quality of mail flow. For example, there is such a dashboard for Postfix logs: [Postfix Delivery Status](https://grafana.com/grafana/dashboards/20574-postfix-delivery-status/)
