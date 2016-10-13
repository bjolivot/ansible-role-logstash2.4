logstash2.4
==================

Brief role description


Role Variables
--------------

Mandatory vars :

    - logstash_input_conf: logstash input configuration
    - logstash_filter_conf: logstash filter configuration
    - logstash_output_conf: logstash output configuration



Default vars
    - logstash_log_dir: where to store log files   (default : /var/log/logstash)
    - logstash_user: user starting lgstash process  (default : logstash)
    - logstash_etc_dir: where to search for config files (default : /ets/logstash/conf.d)
    - logstash_apt_repo: logstash apt-repository (default: https://packages.elastic.co/logstash/2.4/debian)
    - logstash_repo_gpg_key: apt-repository key (default: https://packages.elastic.co/GPG-KEY-elasticsearch)
    


How to use 
----------

- hosts: Logstash
  roles:
    - role: logstash2.4

  vars:
        logstash_input_conf: |
            beats { 
                port => 5044
            }


        logstash_output_conf: |

            elasticsearch {
                hosts => {{ elasticsearch_srv }}
            }


        logstash_filter_conf: |
            geoip { 
                source => "host_ip"
            }


License
-------

Licensed under the MIT License. See the [LICENSE](LICENSE) file for details.


Author Information
------------------

See my other "work on my computer" ansible things on https://www.github.com/bjolivot
