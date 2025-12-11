PostgreSQL + Prometheus + Grafana
=========

набор ролей позволяет установить PostgreSQL, Prometheus, Grafana и пару экспортеров node_exporter c prometheus-postgres-exporter, при этом первый и последний устанавливаются из внешних репозиториев, а для установки остального требуется предварительно скачать патеты или архивы и поместить их в директории `Files` соответствующих ролей. Имена файлов внести в `start.yml`.  
Хранение больших файлов внутри роли скорее является антипаттерном, но таковы были граничные условия выполнения задачи.  
По возможности, лучше выложить файлы на http «шару», на пример развернув nginx и внеся примерно такие изменения:
* добавить переменную
```
  vars:
    grf_paht: "http://192.168.1.3/files/grafana_12.3.0_19497075765_linux_amd64.deb" # http путь до пакета
```

```
- name: install grafana on local
  ansible.builtin.apt:
    deb: "{{ grf_paht }}"
  register: status_packed
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
