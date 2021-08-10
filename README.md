ansible-role-youtubedl-server
=========

Deploy [youtube-dl-server](https://github.com/nbr23/youtube-dl-server) using
docker and nginx.

Role Variables
--------------

- `youtubedl_build_from_repo`: Force docker image build from git repository
- `youtubedl_git_repo`: Url of git repository to build for if
  `youtubedl_build_from_repo` is true or if the platform is not 64bit x86.
- `youtubedl_git_branch`: Use a specific git branch to build from
- `youtubedl_build_youtubedl`: Youtube-dl fork to use (`youtube-dl` or
  `youtube-dlc`) when building from the repo
- `youtubedl_build_atomicparsley`: Add atomicparsley to the image
(necessary for the `--embed-thumbnail` flag)
- `youtubedl_dockerhub_image`: Use a specific image and tag from docker hub
- `youtubedl_container_build_dir`: Temporary directory for docker image build
  if building from repository
- `youtubedl_server_name`: Domain name hosting youtube-dl-server
- `youtubedl_tls_cert_dir`: Directory storing the TLS keychain and private key
- `youtubedl_auth_basic`: Enable basic authentication
- `youtubedl_auth_basic_file_path`: Path to the basic authentication file
- `youtubedl_nginx_allow`: List of nginx allow rules target
- `youtubedl_nginx_deny`: List of nginx deny rules target
- `youtubedl_docker_port`: Port to use for the docker container
- `youtubedl_user_uid`: run container with specific UID
- `youtubedl_user_gid`: run container with specific GID
- `youtubedl_memory_limit`: Memory limitation for the container
- `youtubedl_host_data_dir`: Host directory to mount as data directory.
  Downloaded media will be stored there
- `youtubedl_config_host_location`: If uncommented and set, enables overwriting
  the container's default config.yml file to set own youtube-dl-server settings.
- `ydl_server` and `ydl_options`: Dictionnaries containing your youtube-dl-server
configurations. Refer to the
[youtube-dl-server](https://github.com/nbr23/youtube-dl-server/blob/master/README.md#configuration)
documentation.

Example Playbook
----------------

```
---
- hosts: all
  gather_facts: false
  become: true

  roles:
  - role: ansible-role-youtubedl-server
```


License
-------

MIT
