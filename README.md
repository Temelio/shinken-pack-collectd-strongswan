# shinken-pack-collectd-strongswan

## Description

This Shinken monitoring pack is used to manage strongswan services with our
standard deployment of Collectd.

We request Collectd data using unixsock plugin and collectd-nagios script from
collecd-utils package.

This pack depends to shinken-pack-collectd-base to work and default usage is
for ipsec tunnel management

## Objects

### Templates

#### Host templates

* collectd-strongswan: Manage all default thresholds and values for services

### Services

| Service name                 | Description                | Value specification                            | DS        | Consolidation | Warning variable | Critical variable | Duplicate_foreach variable |
|------------------------------|----------------------------|------------------------------------------------|-----------|---------------|------------------|-------------------|----------------------------|
| Strongswan - $KEY$ processes | Check strongswan processes | processes-$VALUE1$/ps_count                    | processes | none          | $VALUE2$         | $VALUE3$          | _strongswan_processes      |
| Strongswan - $KEY$           | Check listening ports      | tcpconns-$VALUE1$-local/tcp_connections-LISTEN | value     | none          | $VALUE2$         | $VALUE3$          | _strongswan_listen         |

## Default values

    _strongswan_processes   charon $(charon)$$(1:1)$$(1:1)$,starter $(starter)$$(1:1)$$(1:1)$
    _strongswan_listen      Listen 4500 $(4500)$$(1:1)$$(1:1)$,Listen 500 $(500)$$(1:1)$$(1:1)
