

## Sentencias DDL

**Create**

    create database ejemplo;
    use ejemplo;
    create table nombretabla (columnas);
    CREATE TABLE articulo (id_articulo INT NOT NULL PRIMARY KEY
      AUTO_INCREMENT, id_categoria INT NOT NULL, titulo VARCHAR(40)
      NOT NULL, contenido TEXT NOT NULL);​
**Show**

    show tables;
**Drop**

    drop database basedatos;
    drop table tabla;
**Alter**

    
|Sentencia|Descripcion  |
|--|--|
| ALTER TABLE ejemplo ENGINE = InnoDB​ |Cambiar el tipo de motor (engine) de la tabla 'ejemplo'​  |
| ALTER TABLE personas RENAME usuarios​ | Cambia el nomnbre de la tabla 'personas' a 'usuarios'​ |
|ALTER TABLE ejemplo DROP COLUMN nombre​|Elimina la columna 'nombre' de la tabla 'ejemplo'.​|
| ALTER TABLE ejemplo DROP COLUMN nombre, DROP COLUMN paterno​ | Elimina más de una columna.​ |
| ALTER TABLE ejemplo CHANGE monto cantidad FLOAT(8,2) |Cambia el nombre de la columna ‘monto’ al nuevo nombre ‘cantidad’ con la definición del tipo de datos.​  |
| ALTER TABLE ejemplo CHANGE cantidad cantidad FLOAT(10,2)​ | Cambia solo el tipo de datos de la columna, conservando el mismo nombre.​ |
| ALTER TABLE ejemplo MODIFY cantidad FLOAT(10,2)​ | Cambia solo el tipo de datos de la columna, conservando el mismo nombre (igual que el anterior).​ |
| ALTER TABLE ejemplo ADD materno VARCHAR(20) AFTER paterno​ |Añade la columna ‘materno’ después de la columna ‘paterno’.​  |
|ALTER TABLE usuarios ADD FOREIGN KEY(id) REFERENCES entradas(id_user)​  |Añade un ‘Foreign Key’ en la columna ‘id’ de la tabla ‘usuarios’ que apunta a la columna ‘id_user’ de la tabla ‘entradas’.​  |

## Sentencias DML

**Select**
Se usa para obtener datos de una base de datos.

    SELECT column_name, column_name2 FROM table_name;​

**Insert**
Se usa para insertar datos a una tabla.

    INSERT INTO nombre_tabla (columna1,columna2) VALUES
      ('valor1','valor2');​

**Update**
Modifica datos existentes en una tabla.

    UPDATE nombre_tabla SET campo1 = 'valor', campo2 = 'valor2‘​
      WHERE campo1 =*


*Si nos fijamos en la sintaxis del UPDATE es simple, sencillamente indicamos la tabla que deseamos actualizar, cuales son los valores y luego establecemos una condición que indica cual registro actualizar.​ Ojo hay que estar muy atentos al momento de realizar un UPDATE ya que de no establecer esta condición que indica cual registro actualizar se actualizaran todos los registros de nuestra tabla con los valores establecidos.*



**Delete**
Elimina todos los registros de la tabla sin borrar espacios asignados a registros.

    DELETE FROM nombre_tabla WHERE campo = 'valor';​
*La sentencia DELETE borra el campo especificado en la condición, al igual que como se indico con el UPDATE hay que tener en cuenta que si no se indica una condición se borraran todos los registros de la tabla.​*

**Truncate**
Nos sirve para borrar todos los campos de una tabla, tiene algunas diferencias básicas con el DELETE, una de ellas que esta sentencia reinicia los campos auto_incrementos, la sentencia TRUNCATE borra todos los campos de la tabla, sin establecérsele ninguna condición, la sintaxis es la siguiente:

    TRUNCATE TABLE nombre_tabla;
*Como se puede ver en este tipo de sentencia no existe condición ya que es para el borrado completo de una tabla.*

## Foreign Keys
En primer lugar, creamos la tabla ‘clientes’ con los campos ‘id’ y ‘nombre’. Además, el campo ‘id’ es la clave primaria de esta tabla:

    CREATE TABLE `clientes` (`id` int(11) PRIMARY KEY, `nombre` 
      varchar(64) DEFAULT NULL​) ENGINE=InnoDB;
Después, creamos la tabla ‘pedidos’. Esta tabla también tiene un campo ‘id’ que es la clave primaria de esta tabla. Además, tiene un campo ‘idcliente’ que identifica el cliente que ha realizado el pedido:

    CREATE TABLE `pedidos` ( `id` int(11) PRIMARY KEY, `idcliente` 
      int(11) NOT NULL, `idproducto` int(11) NOT NULL) ENGINE=InnoDB;​
Establecemos una restricción entre el campo ‘idcliente’ de la tabla ‘pedidos’ y el campo ‘id’ de la tabla ‘clientes’, de la forma:

    ALTER TABLE pedidos ADD FOREIGN KEY (idcliente)
      REFERENCES clientes (id);​
    ALTER TABLE pedidos ADD CONSTRAINT fk_pedidos FOREIGN KEY (ticket)
      REFERENCES tickets(ticket);​ 
Para eliminar una FK debemos buscar el CONSTRAINT:

    show table nombreTabla;
Una vez obtenido, usamos alter table drop:

    alter table cliente drop FOREIGN KEY cliente_ibfk_1;​
Luego borramos la key que se haya creado como MUL:

    alter table cliente drop  KEY  tc_id;​
**Desactivar FKs**
A veces es necesario desactivar/activar las FKs para poder hacer algunas operaciones. Para hacerlo de forma masiva, usaremos el siguiente comando respectivamente:

    SET FOREIGN_KEY_CHECKS=0;
    SET FOREIGN_KEY_CHECKS=1;




















    


