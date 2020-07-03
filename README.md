# wp-docker
WP docker template, should be used with jwilder/nginx-proxy

## Installation
_If you already have Nginx reverse proxy running like explained in 1. and 2., skip to step 3._
1. First create network for nginx reverse proxy, if it does not exist already.\
`docker network create nginx-proxy`

2. Then run nginx reverse proxy\
`docker run --network nginx-proxy --volume /var/run/docker.sock:/tmp/docker.sock:ro -d jwilder/nginx-proxy`

3. Clone this repo to a new directory\
`git clone git@github.com:valmiste/wp-docker.git ./test-wp`

4. Edit .env file located in wp-docker dir, change variables for passwords and names\
`cd ./test-wp/ && vim .env`

4. Edit your hosts file to include $WP_URL for localhost loopback\
`{ WP_URL=$(grep WP_URL .env | cut -d '=' -f 2-); echo "127.0.0.1 ${WP_URL}.localhost # Added for wp-docker local container" | sudo tee -a /etc/hosts ; }`

5. Run the wp-docker container\
`docker-compose up -d`

Now you should be able to access the wordpress instance with\
http://$wp_url.localhost:400 
