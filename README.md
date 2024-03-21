# Docker NGINX & PHP-FPM Setup

The repo contains the files needed to quickly get up and running with a local PHP development Docker container. The container uses NGINX for the server, local volumes for the files and database, and nginx-proxy to configure the local HTTPS protocol.

## Usage

### First Time Setup

For all features to work, you must do a one-time setup of the following:

1. Make sure the following command line tools are installed:
    - [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
    - [mkcert](https://github.com/FiloSottile/mkcert)
2. To use multiple local domains on the standard 80 or 443 ports, create a stand-alone reverse proxy network:
    - In the parent directory where you want to store your network files (such as `/Users/Name/Projects/Assets/Docker/`), run: `git clone git@github.com:jacobcassidy/docker-localhost-network.git`.
    - From the `docker-localhost-network` directory you cloned, run: `docker compose up -d` to create the container.

### Continued/Additional Setup

1. Run `git clone git@github.com:jacobcassidy/docker-nginx-phpfpm-setup.git` in the parent directory where you want your project directory nested.
2. Rename the cloned directory from "docker-nginx-phpfpm-setup" to your project name.
3. Rename the `.env-example` file to `.env`.
4. Update the `.env` file with the database password and port number, as well as the local domain your project will use.
5. In the `/localhost-network/certs` directory you created in the __First Time Setup__ instructions above, create SSL certs for the HTTPS protocol using the command: `mkcert yourdomain.localhost`. Make sure you replace "yourdomain.localhost" with the local domain name you specified in your `.env` file.
6. Rename the created certs from `yourdomain.localhost-key.pem` to `yourdomain.localhost.key` and `yourdomain.localhost.pem` to `yourdomain.localhost.crt`
7. Open the [Docker Desktop](https://www.docker.com/products/docker-desktop/) app so the Docker engine is on.
8. Build the docker container with: `docker compose up -d` (run this command in the `/docker` directory). This will create your server and add the `/storage/mysql` directory in your docker directory.
9. Replace this __Docker NGINX & PHP-FPM Setup__ README content with your project name and description (you can view the original Docker WordPress Setup README [here](https://github.com/jacobcassidy/docker-nginx-phpfpm-setup)).
10. Remove the original "docker-nginx-phpfpm-setup" .git directory with: `rm -rf .git` (run this in your project directory).
11. Initialize a new git repository for your project with: `git init`.
12. If you will use a GitHub remote repo, create and connect to it now.
13. Open your browser to the local domain specified in your `.env` file and complete the WordPress installation.

## Issues?

If you come across any issues, please feel free to report them [here](https://github.com/jacobcassidy/docker-nginx-phpfpm-setup/issues).
