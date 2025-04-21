 assignment

## Requirements:

- Docker
- Docker Compose
- Update your `/etc/hosts` file:
127.0.0.1 gitea.local grafana.local

  

  ## Step-by-Step Instructions:

### 1. Clone the Repo

git clone https://github.com/nishantnesargi13/assignment.git


cd assignment

## **2. Configure Authelia**

Edit `data/authelia/config/configuration.yml` and define:

- **JWT secret**
- **Authentication backend** 
- Access control rules (for gitea.local, grafana.local)



# 3. Create Authelia User
Edit data/authelia/config/users_database.yml

users:
  nishant:
    displayname: Nishant
  
    password: <hashed-password>
   
    email: nishant@example.com

Generate hashed password using:docker run authelia/authelia:latest authelia hash-password 'your-password'

## *4. Nginx Proxy Config*

Shared Proxy Config

data/nginx/proxy-confs/proxy.conf/

  a)Gitea Proxy Config
data/nginx/site-confs/gitea.local.conf

  b)Grafana Proxy Config
data/nginx/site-confs/grafana.local.conf


## 5. Launch Services
Run the following:
docker-compose up -d

Services will be available at:

Gitea → http://gitea.local

Grafana → http://grafana.local


Default Login
Use the credentials from users_database.yml
Username: nishant
Password: <your password>




## Notes:
You must have gitea.local and grafana.local in your /etc/hosts file.

Password must be hashed using Authelia's hash tool.

Make sure no other service is using port 80.**
