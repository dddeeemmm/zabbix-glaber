zabbix-glaber
=========

    Install and configure Zabbix (Glaber)

Role Variables
--------------

    zabbix_install:                         [ default: true ] install packages

    zabbix_db_host: ''                      [ required ] database host
    zabbix_dp_port: ''                      [ required ] database port
    zabbix_db_name: ''                      [ required ] database name
    zabbix_db_user: ''                      [ required ] database user
    zabbix_db_password: ''                  [ required ] database password
    zabbix_history_storage_url: ''          [ required ] clickhouse url
    zabbix_history_storage_db_name: ''      [ required ] clickhouse database name
    
    zabbix_start_db_syncers:                [ default: 30 ] database syncers
    zabbix_log_file_size:                   [ default: 1024 ] log file size
    zabbix_date_timezone:                   [ default: Europe/Moscow ] timezone 
    zabbix_clickhouse_disable_nanoseconds:  [ default: 1 ] disable store nanoseconds
    zabbix_clickhouse_preload_values:       [ default: 8 ] preload metrics to clickhouse buffer table after restart server
    zabbix_clickhouse_fill_time:            [ default: 300 ] denied history read before that most metrics would get enough value cache 
    zabbix_start_pollers_async_snmp:        [ default: 6 ] async snmp pollers
    zabbix_start_pollers_async_agent:       [ default: 6 ] async agent pollers
    zabbix_start_pingers:                   [ default: 10 ] pingers
    zabbix_start_discoverers:               [ default: 10 ] discoverers
    zabbix_start_pollers_unreachable:       [ default: 10 ] unreachable pollers
    zabbix_start_pollers:                   [ default: 10 ] pollers
    zabbix_cache_size:                      [ default: 226M ] cache size
    
    nolog:                                  [ default: true ] disable log secrets

Example Playbook
----------------

    - hosts: zabbix_cluster
      become: true
      vars:
        zabbix_db_host: postgres.domain.org
        zabbix_dp_port: 5432
        zabbix_db_name: zabbix
        zabbix_db_user: zabbix
        zabbix_db_password: zabbix
        zabbix_history_storage_url: clickhouse.domain.org
        zabbix_history_storage_db_name: zabbix
      roles:
        - { name: zabbix-glaber, tags: zabbix }
    
License
-------

    MIT

Author Information
------------------

    Dmitrij Petrov
