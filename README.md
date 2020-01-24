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

## LINUX /MOUNT /FSTAB

#### para montar un disco de forma permanente se debe modificar el archivo */etc/fstab*. Para montarlo live se ejecuta el siguiente comando:

````
mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport DIRECCION_URL_O_IP:/ NOMBRE_FOLDER
````

