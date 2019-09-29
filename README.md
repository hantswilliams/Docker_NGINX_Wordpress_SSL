# Deploying Secure (HTTPS) Wordpress site via Ansible, Docker, and NGINX 

## Primary Technologies Utilized 
- Ansible 
- Docker 
- NGINX 
- Wordpress
- LetsEncrypt 

## Step 1: Ansible 
- Create new instance using ansible playbook (from datasci project, installing docker and docker-compose

## Utilizating two reports:

### Step 2: Installing Repo 1
- Install Docker/Nginx/LetsEncrypt file: https://github.com/evertramos/docker-compose-letsencrypt-nginx-proxy-companion
- Install this in a new mkdir called `nginx_docker_deploy`

### Step 3: Installing Repo 3 
- Install Docker/Wordpress/LetsEncrypt file: https://github.com/evertramos/docker-wordpress-letsencrypt
	- install this in a new mkdir called `wordpress_docker_deploy`
- Modify this one based off of: https://medium.com/today-i-solved/wordpress-over-https-with-docker-ssl-ecaf02a47fea
- Edit the .env file to match the new passwords, db names, etc....
- Edit the docker-compose file twith new passwords, db names, etc...that match the env file 
- Side note --> when going into these docker images, might need to perform `apt-get updated` followed by `apt-get install nano` if your text editor is not installed
- Edit the file size --> need to go into nginx docker container and modify `/etc/nginx/conf.d`
- Need to add below line, per https://www.cyberciti.biz/faq/linux-unix-bsd-nginx-413-request-entity-too-large/ to the nginx configuration file:
	- `client_max_body_size 50M;`
- Then perform: 
	- `service nginx reload`
- Then go into docker-wordpress into html folder and do
	- chmod 777 wp-content/
- This should then have fixed anything to do with file size limits 


