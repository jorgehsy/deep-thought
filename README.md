# deep-thought
Este es un readme con todos las guías, comandos, tips y trastornos útiles que me he encontrado a lo largo del trabajo y que ayudan a hacer y solucionar 'cosas'

## MYSQL / DATABASES

#### importar una base de datos desde un dump gigante con varias bases de datos

> Extraer la base de datos del dump con este comando

````bash
sed -n '/^-- Current Database: `BASE_DE_DATOS`/,/^-- Current Database: `/p' NOMBRE_DEL_DUMP_GIGANTE.sql > ARCHIVO_DESTINO.sql
````
> Luego importar el dump por un UI o por consola 

````bash
mysql -h 127.0.0.1 -u root -psecret BASE_DE_DATOS < DUMP.sql
````

#### bash script para hacer backup de la masede datos mysql
````bash
export $(egrep -v '^#' /var/www/proyecto/.env | xargs)
mysqldump -u $DB_USERNAME -p$DB_PASSWORD $DB_DATABASE > /var/www/proyect/$DB_DATABASE-$(date +"%m-%d-%y-%T").sql
````

## LINUX /MOUNT /FSTAB /PERMISSIONS

#### para montar un disco de forma permanente se debe modificar el archivo */etc/fstab*. Para montarlo live se ejecuta el siguiente comando:

````
mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport DIRECCION_URL_O_IP:/ NOMBRE_FOLDER
````

#### estos comandos corrigen los permisos de los archivos, donde el usuario pertenece al mismo grupo de apache/nginx
***IMPORTANTE*** verificar la ruta de la carpeta

  para archivos
````
sudo find ./ -type f -exec chmod 664 {} \;
````
  para carpetas
````
sudo find ./ -type d -exec chmod 775 {} \;
````
## NPM
 
Aveces da error el npm install, arrojando el siguiente emnsaje "Error: EACCES: permission denied open '/Users/xxxx/.npm/", puede ser por problemas de permisos en la carpeta del user, se soluciona ejecutando el siguiente comando:

````
sudo chown -R $(whoami) ~/.npm
````

