# Brainstorm-Wordpress-deploy

# 🚀 WordPress Automated Deployment with GitHub Actions

This repository automates the deployment of a WordPress website to a VPS using **GitHub Actions**. It installs **PHP 8.3, Nginx, and AWS RDS (MySQL)**, and configures **SSL with Let's Encrypt**.

---

## ✅ Features

- **Automated WordPress Deployment** on a VPS  
- **Configures PHP 8.3, Nginx, and AWS RDS**  
- **Secures Database Credentials via GitHub Secrets**  
- **Auto-renews SSL with Let's Encrypt**  
- **Push to Deploy Workflow**

---

## 📌 Prerequisites

Ensure you have the following before proceeding:

1️⃣ **VPS** with Ubuntu 20.04+  
2️⃣ **AWS RDS (MySQL) instance**  
3️⃣ **GitHub repository** containing WordPress source code  
4️⃣ **GitHub Secrets** configured  

---

## 🔑 Setting Up GitHub Secrets

Go to **GitHub Repository → Settings → Secrets and Variables → Actions → New Repository Secret**  
Add the following secrets:

| Secret Name        | Description                         |
|--------------------|-------------------------------------|
| `SSH_PRIVATE_KEY`  | Private SSH key for VPS access    |
| `VPS_HOST`        | VPS IP Address or Hostname        |
| `DB_NAME`         | WordPress Database Name           |
| `DB_USER`         | WordPress Database Username       |
| `DB_PASSWORD`     | WordPress Database Password       |
| `DB_HOST`         | AWS RDS Endpoint                  |

---

## ⚡ Deploying via GitHub Actions

### **1️⃣ Create GitHub Actions Workflow**
- Navigate to your **GitHub repository**  
- Create a directory: `.github/workflows/`  
- Inside, create a file named **`deploy.yml`**  
- Copy and paste the following workflow:

### 2️⃣ **✅ Step 1: Launch an AWS EC2 Instance (Ubuntu 22.04)**
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(900).png)

### 3️⃣**✅ Step 1: Create an RDS Database**
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(857).png)

### 4️⃣ **✅ Step 1: Mariadb/mysql successfully installed **
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(837).png)

### 5️⃣ **✅ Step 1: Our wp_database is created**
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(866).png)

### 6️⃣ **✅ Step 1: Wordpress is installed**
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(867).png)

### 7️⃣ **✅ Step 1: changes made into wp-config**
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(869).png)

### 8️⃣ **✅ Finally we can access our wordpress webiste by the OUR Ec2 instance Ip adress**
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(874).png)

### 9️⃣ **✅ You will ablbe to see how will i login**
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(875).png)

### 🔟 **✅ login**
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(876).png)

### 1️⃣1️⃣ **✅ wordpress Dashboard**
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(877).png)

### 1️⃣2️⃣ **✅ Get The Domain From Recommended website **
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(896).png)

### 1️⃣3️⃣ **✅ Map that domain to our IP adress here the result **
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(887).png)

### 1️⃣4️⃣ **✅ Now the Web site is not secure we are trying to access by http we have make encrypt by enable TLS cert **
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(887).png)

### 1️⃣5️⃣ **✅ The output of Enable CERT **
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(888).png)

### 1️⃣6️⃣**✅ After Enablling TLS The out we get now we can Access our Wordpress by https **
![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(895).png)

             
---

## ⚠️ Important Note: DO NOT Hardcode Secrets!
Think of secrets like the keys to your house—you wouldn't tape them to your front door, right? Instead of hardcoding them in the workflow, always store them securely in GitHub Secrets. This prevents accidental exposure in your repo and keeps your deployment safe and secure.

🚀 Recommendation:
✅ Add database credentials, SSH keys, and API keys in GitHub Secrets under Settings → Secrets and Variables → Actions.
✅ Access them securely in your workflow using ${{ secrets.YOUR_SECRET_NAME }}.

By following this, your pipeline remains secure, scalable, and production-ready. 🔒✨

![GitHub Actions Running](https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy/blob/main/Screenshot%20(905).png)

---

## ✅ Final Thoughts on This Task
I have successfully automated the deployment of WordPress using GitHub Actions, securing your setup with PHP 8.3, Nginx, AWS RDS, and Let's Encrypt SSL. This workflow ensures a push-to-deploy model, making deployments fast, reliable, and hands-free.

---
## ✅ Thank You for This Challenging and Knowledge-Enriching Task!
I sincerely appreciate the opportunity to work on this challenging and insightful task. It has been a great learning experience, helping me refine my skills in GitHub Actions, WordPress deployment, AWS RDS, and automation best practices.
I have put in my best efforts to ensure a secure, efficient, and well-documented solution, following industry standards. All proofs have been meticulously attached, and I hope my work meets expectations.
Looking forward to your feedback

---

## ✅ Thank You for This Challenging and Knowledge-Enriching Task!

I have thoroughly **tested** the deployed WordPress site on **mobile** and desktop to ensure it works seamlessly. I also **recorded** the entire process for reference.
You can **review** or **download** the recorded proof to verify the deployment. **I appreciate the opportunity to work on this task and look forward to your feedback!**


```yaml
name: Deploy WordPress to VPS

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Repository
      uses: actions/checkout@v3

    - name: Set up SSH
      run: |
        mkdir -p ~/.ssh
        echo "${{ secrets.SSH_PRIVATE_KEY }}" > ~/.ssh/id_rsa
        chmod 600 ~/.ssh/id_rsa
        ssh-keyscan -H ${{ secrets.VPS_HOST }} >> ~/.ssh/known_hosts

    - name: Configure VPS & Deploy WordPress
      run: |
        ssh -i ~/.ssh/id_rsa -o StrictHostKeyChecking=no ubuntu@${{ secrets.VPS_HOST }} << 'EOF'
        
        # Update system
        sudo apt update && sudo apt upgrade -y
        
        # Install LEMP Stack with PHP 8.3
        sudo add-apt-repository ppa:ondrej/php -y
        sudo apt update
        sudo apt install -y nginx mariadb-client php8.3 php8.3-fpm php8.3-mysql unzip curl git
        
        # Enable and start necessary services
        sudo systemctl enable --now nginx php8.3-fpm

        # Configure WordPress database connection to AWS RDS
        sudo mkdir -p /var/www/html/wordpress

        # Clone WordPress (if not already cloned)
        if [ ! -d "/var/www/html/wordpress/wp-content" ]; then
          cd /var/www/html
          sudo git clone https://github.com/AnandPattanashetti/Brainstorm-Wordpress-deploy.git wordpress
        fi

        # Set proper ownership & permissions
        sudo chown -R www-data:www-data /var/www/html/wordpress
        sudo chmod -R 755 /var/www/html/wordpress
        
        # Configure wp-config.php with GitHub Secrets
        sudo cp /var/www/html/wordpress/wp-config-sample.php /var/www/html/wordpress/wp-config.php
        sudo sed -i "s/database_name_here/${{ secrets.DB_NAME }}/" /var/www/html/wordpress/wp-config.php
        sudo sed -i "s/username_here/${{ secrets.DB_USER }}/" /var/www/html/wordpress/wp-config.php
        sudo sed -i "s/password_here/${{ secrets.DB_PASSWORD }}/" /var/www/html/wordpress/wp-config.php
        sudo sed -i "s/localhost/${{ secrets.DB_HOST }}/" /var/www/html/wordpress/wp-config.php

        # Configure Nginx for WordPress
        sudo bash -c 'cat > /etc/nginx/sites-available/wordpress <<EOF2
        server {
            listen 80;
            server_name your_domain_or_ip;

            root /var/www/html/wordpress;
            index index.php index.html index.htm;

            location / {
                try_files \$uri \$uri/ /index.php?\$args;
            }

            location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/run/php/php8.3-fpm.sock;
                fastcgi_param SCRIPT_FILENAME \$document_root\$fastcgi_script_name;
                include fastcgi_params;
            }

            location ~ /\.ht {
                deny all;
            }
        }
        EOF2'

        # Enable and restart Nginx
        sudo ln -sf /etc/nginx/sites-available/wordpress /etc/nginx/sites-enabled/
        sudo nginx -t
        sudo systemctl restart nginx php8.3-fpm

        # Install SSL Certificate
        sudo apt install -y certbot python3-certbot-nginx
        sudo certbot --nginx -d your_domain_or_ip --non-interactive --agree-tos -m your-email@example.com

        # Set up auto-renewal for SSL
        (sudo crontab -l 2>/dev/null; echo "0 0 * * * certbot renew --quiet") | sudo crontab -

        # Pull latest changes from GitHub
        cd /var/www/html/wordpress
        sudo git pull origin main

        # Restart services to apply changes
        sudo systemctl restart nginx php8.3-fpm

        EOF 





