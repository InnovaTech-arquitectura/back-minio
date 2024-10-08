# back-minio

Este proyecto configura un contenedor de MinIO utilizando Docker Compose. MinIO es un almacenamiento de objetos compatible con Amazon S3.

## Requisitos

- Docker
- Docker Compose

## Configuración

El archivo `Docker-compose.yaml` configura un servicio de MinIO con las siguientes características:

- Imagen: `minio/minio`
- Nombre del contenedor: `minio`
- Variables de entorno:
  - `MINIO_ROOT_USER`: minioadmin
  - `MINIO_ROOT_PASSWORD`: minioadminpassword
- Volúmenes:
  - `./data:/data`: Mapea el almacenamiento en tu máquina local
- Puertos:
  - `9000:9000`: Puerto para la API de MinIO
  - `9001:9001`: Puerto para la consola de administración
- Reinicio automático: `always`
- Comando: `server /data --address ":9000" --console-address ":9001"`

## Uso

1. Clona este repositorio.
2. Navega al directorio del proyecto.
3. Ejecuta el siguiente comando para iniciar el contenedor de MinIO:

    ```sh
    docker-compose up -d
    ```

4. Accede a la consola de administración de MinIO en [http://localhost:9001](http://localhost:9001) con las credenciales configuradas (`minioadmin` / `minioadminpassword`).

## Detener el contenedor

Para detener y eliminar el contenedor, ejecuta:

```sh
docker-compose down