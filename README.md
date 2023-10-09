# Angular_ionic_deployment


## 1. Setup your ec2 instance 
- Setup ec2 instance by selecting os image and instance type

## 2. Clone your project from GitHub

``` 
    sudo git clone <user repo link>
```

## 3. Change the security setting for accessing your website 
 ![WhatsApp Image 2023-10-09 at 1 18 04 PM](https://github.com/Sakibdevlekar/nodeJs_Deployment_setup/assets/111329075/f8e0b642-3453-41a2-bb52-37b45017667c)

 

### Then click on **edit inbound rule**  and add some rules
- Add same rule shown as in the image


![image](https://github.com/Sakibdevlekar/angular_ionic_deployment/assets/111329075/0e49fadc-841d-471d-bf22-876aec7ba2a8)

## 4. Install NGINX and configure
  ```
     sudo apt install nginx
  ```
  ``` 
     sudo nano  /etc/nginx/sites-available/default 
  ```
- Add the following to the location part of the server block
  ```
  server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /var/www/html;

        index index.html ;

        server_name _;

        location / {

                try_files $uri $uri/ /index.html  =404;
        }
  ```
  
  ### - Check NGINX config
  ```
     sudo nginx -t
  ```
  
  ### - Restart NGINX
  ```
     sudo systemctl restart nginx
  ```

  ## Check sites-enabled  and sites-available files data are the same. To check sites-enabled
  ```
  sudo nano  /etc/nginx/sites-enabled/default 
  ```
- Again restart nginx
  ```
     sudo systemctl restart nginx
  ```


  ### - Check status  of NGINX
  ```
     sudo systemctl status nginx
  ```

  ## 5. Now  copy past the public IP of your instance your site home page is visible now which means your app is hosted successfully ✨
