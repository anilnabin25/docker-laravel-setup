# How to create a docker

Lets suppose the project folder is *laravel* and the *laravel* folder is inside the *project*

1. Copy all the files of this folder to the project folder

2. Go to the project folder and open terminal using (ctl+shift+T) and type the below command
 > divya@ubuntu:~/project$ git clone https://github.com/laravel/laravel.git laravel\
  (this command will create the clone of the laravel project from the github)

 > divya@ubuntu:~/project$ sudo chown -R $USER:$USER laravel\
 (this command will grant permission to the user to acces the folder )

 > divya@ubuntu:~/project$ cd laravel\
 ( this command will helps you to enter the laravel folder)

 > divya@ubuntu:~/project/laravel$ docker run --rm -v $(pwd):/app composer install\
 (this command will is to install the vendor file)  

 > divya@ubuntu:~/project/laravel$  code .\
 (this will open the project on visual code editor)

3. Open the *docker-compose.yml* and find the *MYSQL_DATABASE* and *MYSQL_ROOT_PASSWORD* & provide a new one for example i am using *laravel* *password*

 > MYSQL_DATABASE: laravel\
 > MYSQL_USER: laravel\
 > MYSQL_PASSWORD: password\
 > MYSQL_ROOT_PASSWORD: password

4. Now copy the *env-example* to *.env* using below command
 > divya@ubuntu:~/project/laravel$ cp .env.example .env

5. Now edit the newly created *.env* file value
> DB_CONNECTION=mysql\
> DB_HOST=db\
> DB_PORT=3306\
> DB_DATABASE=laravel\
> DB_USERNAME=laravel\
> DB_PASSWORD=password\

6. Now run the below command to create a docker image
 > divya@ubuntu:~/project/laravel$ docker-compose up -d

7. As a final step, visit http://your_server_ip in the browser. You will see the following home page for your Laravel application:(if you are using in the locall http://localhost) if you change the port in the *ports* of webserver then  *:ports_no*  will be added

8. Some of the usefull commands
 > divya@ubuntu:\~/project/laravel$ docker ps => to check the currently running docker\
 > divya@ubuntu:\~/project/laravel$ docker-compose up -d => to create docker container\
 > divya@ubuntu:\~/project/laravel$ docker-compose exec app php artisan key:generate => to generate the artisan php key\
 > divya@ubuntu:\~/project/laravel$ docker-compose exec app php artisan config:cache => to clear the configuration


For more informatrion please click [here](https://www.digitalocean.com/community/tutorials/how-to-set-up-laravel-nginx-and-mysql-with-docker-compose)
