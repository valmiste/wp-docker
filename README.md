# wp-docker
WP docker template, should be used with jwilder/nginx-proxy

## Installation
1. First create network for nginx reverse proxy, if it does not exist already
`docker network create nginx-proxy`

2. Then run nginx reverse proxy
`docker run -network nginx-proxy jwilder/nginx-proxy`

3. Edit .env file located in wp-docker dir, change variables for passwords and names

4. Edit your hosts file to include $WP_URL
`sudo echo "127.0.0.1 $WP_URL" >> /etc/hosts`

5. Run the wp-docker container 
`docker-compose up -d`

