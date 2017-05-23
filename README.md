# docker-rancher-cli

Docker image with rancher CLI installed.

Rancher CLI is a client for communicating with Rancher.

More information on the official Rancher documentation: https://docs.rancher.com/rancher/v1.2/en/cli/ and on the Rancher CLI GitHub repository: https://github.com/rancher/cli

# Where to find the Rancher CLI Images
https://hub.docker.com/r/rovecom/rancher-cli/

# How do you use this image?

**Not interactive and basic mode:**

Just run it as a normal command, sharing the directory containing your docker-compose.yml file and your rancher-compose.yml file:

```bash
$ docker run -v /absolute/path/to/project/dir/:/app:ro \
             -e "RANCHER_URL=http://<rancher_server_ip>:<rancher_server_port>" \
             --rm \
             rovecom/rancher-cli:latest 
             rancher --help
```

**Not interactive with custom docker-compose file, rancher-compose file and project name:**

Add the -f, -r, -p options

```bash
$ docker run -v /absolute/path/to/project/dir/:/app:ro \
             -e "RANCHER_URL=http://<rancher_server_ip>:<rancher_server_port>/v1" \
             --rm \
             rovecom/rancher-cli:latest \
             -f "<docker_compose_file_name>.yml" \
             -r "<rancher_compose_file_name>.yml" \
             -p "<project_name>" \
             rancher --help
```

**Not interactive with access control:**

Set the RANCHER_ACCESS_KEY and RANCHER_SECRET_KEY environment variables

```bash
$ docker run -v /absolute/path/to/project/dir/:/app:ro \
             -e "RANCHER_URL=http://<rancher_server_ip>:<rancher_server_port>/v1" \
             -e "RANCHER_ACCESS_KEY=<rancher_access_key>" \
             -e "RANCHER_SECRET_KEY=<rancher_secret_key>" \
             --rm \
             rovecom/rancher-cli:latest
             rancher --help
```

