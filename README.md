# Ansible role for ccollect


Setup ccollect.

## Requirements

- systemd

## Role Variables

see defaults/main.yml

## Dependencies

None.

## Example Playbook

Example:

    - hosts: all
      become: yes
      roles:
      - role: znz.ccollect
        ccollect_conf_name: "myservice"
        ccollect_conf: "/srv/ccollect/conf"
        ccollect_runner_user: "mysrvuser"
        ccollect_runner_group: "mysrvgroup"
        ccollect_sources:
        - name: "myservice.example.jp_uploads"
          source: "myservice.example.jp:/srv/myservice.example.jp/uploads"
          destination: "/srv/ccollect/destination/myservice.example.jp/uploads"
          pre_exec: yes
          post_exec: yes
          rsync_options: "--one-file-system"
          delete_incomplete: yes
          summary: yes
        - name: "myservice.example.jp_log"
          source: "myservice.example.jp:/srv/myservice.example.jp/log"
          destination: "/srv/ccollect/destination/myservice.example.jp/log"
          pre_exec: yes
          post_exec: yes
          rsync_options: "--one-file-system"
          delete_incomplete: yes
          summary: yes
        - name: "myservice.example.jp_db_dump"
          source: "myservice.example.jp:/srv/myservice.example.jp/db_dump"
          destination: "/srv/ccollect/destination/myservice.example.jp/db_dump"
          pre_exec: yes
          post_exec: yes
          rsync_options: "--one-file-system"
          delete_incomplete: yes
          summary: yes
        ccollect_destinations:
        - /srv/ccollect/destination
        ccollect_slack_webhook_url: "https://hooks.slack.com/services/XXXXXX/XXXXXXXX/XXXXXXXXXXXXXXX"

## License

MIT License
