Estas notas son una investigación revisando la documentación oficial ya que no he encontrado nada similar por internet. El objetivo es llevar las prácticas tan conocidas de seguridad de entornos cloud como AWS o Azure a entornos más desconocidos (por lo menos en España). Se agradece la corrección de cualquier error.

---

# Aliyun-Security-Research

Aliyun CLI (Alibaba Cloud Command Line Interface) es una herramienta que permite a los usuarios interactuar con los servicios de Alibaba Cloud desde la línea de comandos. Proporciona una forma conveniente de realizar operaciones en Alibaba Cloud sin necesidad de utilizar la consola web. Con Aliyun CLI, los usuarios pueden gestionar recursos, automatizar tareas y realizar operaciones en múltiples servicios de Alibaba Cloud como Elastic Compute Service (ECS), Object Storage Service (OSS), etc.

Documentación de Aliyun: https://www.alibabacloud.com/help/en

## Roles



## Almacenamiento

### Buckets 

* Listar Buckets
 ```
aliyun oss ListBuckets
```

Nos devolverá algo así

```
{
    "Buckets": {
        "Bucket": [
            {
                "Name": "Totodile",
                "CreationDate": "2023-07-15T08:30:00.000Z",
                "Location": "oss-cn-beijing"
            },
            {
                "Name": "Charmander",
                "CreationDate": "2020-08-01T11:45:00.000Z",
                "Location": "oss-us-west-1"
            }
        ]
    }
}
```
Algo muy importante en cualquier entorno cloud es comprobar los accesos de los buckets (contenedores/blobs en azure)

```
aliyun oss GetBucketAcl --bucket <nombre-del-bucket>
```
Dicho comando nos delvolverá algo similar a esto
```
{
  "RequestId": "ABC123456789",
  "Acl": "public-read"
}
```
Los posibles valores para el ACL son:

* private: Sólo el propietario del bucket tiene acceso
* public-read: Todos pueden leer los objetos dentro del bucket, pero sólo el propietario puede escribir
* public-read-write: Todos pueden leer y escribir en el bucket

### Bases de datos

Aliyun ofrece diferentes bases de datos como RDS (Relational Database Service), PolarDB, o ApsaraDB for Redis entre otras.

* Listar instancias RDS
```
aliyun rds DescribeDBInstances
```

* Listar base de datos
```
aliyun rds DescribeDatabases --DBInstanceId <ID-de-la-instancia>
```

Para otros servicios como PolarDB o Redis usariamos los siguientes comandos

```
aliyun polardb DescribeInstances
```

```
aliyun r-kvstore DescribeInstances
```

## Seguridad







