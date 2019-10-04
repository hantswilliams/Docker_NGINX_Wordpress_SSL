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
-- install this in a new mkdir called `nginx_docker_deploy`

### Step 3: Installing Repo 3 
- Install Docker/Wordpress/LetsEncrypt file: https://github.com/evertramos/docker-wordpress-letsencrypt
-- install this in a new mkdir called `wordpress_docker_deploy`
-- modify this one based off of: https://medium.com/today-i-solved/wordpress-over-https-with-docker-ssl-ecaf02a47fea
-- edit the .env file to match the new passwords, db names, etc....
-- edit the docker-compose file twith new passwords, db names, etc...that match the env file 

### Step4: Test that server is up and running
-- perform docker-compose within folder
-- may need to start, stop, and then re-start to be able to access {websitename}/wp-admin

### Step5: Reconfiguring UPLOAD limit sizes 
-- to edit the file size --> need to go into nginx docker container and modify `/etc/nginx/conf.d` --> `default.conf` file 
-- need to add below line, per https://www.cyberciti.biz/faq/linux-unix-bsd-nginx-413-request-entity-too-large/ to the nginx configuration file:
	-- below should be done/added the below within of the `location /` lines for server's
		--- `client_max_body_size 50M;`
-- then perform: 
	- `service nginx reload`
-- then go into docker-wordpress into html folder and do
	- chmod 777 wp-content/
-- this should then have fixed anything to do with file size limits 


