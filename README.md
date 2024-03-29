# Treafik Setup Helper

## Prerequisites

1. Install docker

2. Init docker swarm
    ```bash
    docker swarm init
    # or
    docker swarm init --advertise-addr 127.0.0.1
    ```
3. Create docker network name `proxy`

    ```bash
    docker network create --attachable --driver overlay proxy
    ```

## Deploy 

> deploy `traefik` and `portainer`
> 
> expose default port: `80`, `443` and `8080`
> 


1. Clone the repository
    ```bash
    git clone https://github.com/attapon-th/traefik-setup.git traefik
    ```

2. Go to the directory
    ```bash
    cd traefik
    ```

3. Create Logs folder (required `sudo`)
    ```bash
    sudo mkdir /var/log/traefik
    ```

4. Gen Self-Signed for traefik
    ```bash
    ./gen-cert.sh
    ```

5. run docker stack 

    > edit: `vi docker/traefik-stack.yml`
    > 
    ```bash
    docker stack deploy -c traefik-stack.yaml traefik
    ```

6. run portainer

    ```bash
    docker stack deploy -c portainer-stack.yaml portainer
    ```


## Using Default setup

>  Portainer: [https://localhost/portainer](https://localhost/portainer)
>
> Traefik Dashboard: [https://localhost:8080/dashboard](https://localhost:8080/dashboard)