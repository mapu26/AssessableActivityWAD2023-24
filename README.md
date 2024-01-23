# AssessableActivityWAD2023-24
### Pasos seguidos para instalar php, mysql, la aplicacion:

1. sudo apt-get update
2. sudo apt-get install mysql-server php libapache2-mod-php php-mysql
3. sudo wget -U "Firefox" "https://phpgurukul.com/?sdm_process_download=1&download_id=7210" -O hostel.zip
4. sudo apt-get install unzip
4. unzip hostel.zip

#### Cambio nombre al directorio y lo copio dentro de /html:

5. sudo mv Hostel\ management\ System\ Proyect/ hostel
6. sudo mv hostel/ /var/www/html/

#### Entro en Mysql, para cambiar la configuracion y no me pida la contraseña:

7. sudo service mysql start
8. sudo mysql
9. USE mysql;
10. UPDATE user SET plugin='mysql_native_password' WHERE User='root';
11. FLUSH PRIVILEGES;
12. exit
13. sudo service mysql restart

#### Doy permisos al directorio hostel de www-data y copio el fichero hodtel.sql a home:

14. sudo chown -R www-data /var/www/htmal/hostel/
15. sudo mv hostel.sql ~

#### Volvemos a entrar en mysql, para crear la base de datos y poblarla:

16. mysql -u root
17. CREATE DATABASE hostel;
18. USE hostel;
19. source /home/ubuntu/hostel.sql

#### Vamos a crear el VirtualHost, lo modificamos y habilitarlo:

20. sudo cp 000-default.conf hostel.conf
21. sudo s2ensite hostel.conf
22. sudo a2dissite 000-default.conf
23. sudo service apache2 restart

### Pasos para la creación del repositorio

#### Crear las claves SSH:

24. ssh-keygen -t rsa -C "Cuenta AWS"

#### Paso el fichero id_rsa.pub a mi pc para copiar el contenido:

25. scp -i labsuser.pem ubuntu@34.235.72.148:/home/ubuntu/.ssh/id_rsa.pub .

#### Creamos un nuevo repositorio publico sin el README
#### Pasos para subir los dos ficheros al repositorio

26. sudo mkdor githostel
27. sudo cp /etc/apache2/sites-available/hostel.conf /home/ubuntu/githostel
28. echo "#AssessableActivityWAD2023-24" >> README.md
29. git init
30. git add .
31. git commit -m "Primer commit"
32. git branch -M main
33. git remote add origin https://github.com/mapu26/AssessableActivityWAD2023-24.git

#### Para poder autentificarme con el token:

34. got remote set-url origin https://mi-token@github.com/mapu26/AssessableActivityWAD2023-24.git
35. git push -u origin main
