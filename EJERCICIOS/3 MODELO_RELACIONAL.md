Se desea diseñar una base de datos para almacenar y gestionar la información
empleada por una empresa dedicada a la venta de automóviles, teniendo en cuenta los
siguientes aspectos:
La empresa dispone de una serie de coches para su venta. Se necesita conocer la
matrícula, marca y modelo, el color y el precio de venta de cada coche.
Los datos que interesa conocer de cada cliente son el NIF, nombre, dirección, ciudad y
número de teléfono: además, los clientes se diferencian por un código interno de la
empresa que se incrementa automáticamente cuando un cliente se da de alta en ella. Un
cliente puede comprar tantos coches como desee a la empresa. Un coche determinado
solo puede ser comprado por un único cliente.
El concesionario también se encarga de llevar a cabo las revisiones que se realizan a
cada coche. Cada revisión tiene asociado un código que se incrementa automáticamente
por cada revisión que se haga. De cada revisión se desea saber si se ha hecho cambio de
filtro, si se ha hecho cambio de aceite, si se ha hecho cambio de frenos u otros. Los
coches pueden pasar varias revisiones en el concesionario

![image](https://user-images.githubusercontent.com/113805099/221386186-28077951-78c3-4da2-8e44-47cf5a78ecbd.png)

POSIBLE CREACION DE TABLAS

CREATE DATABASE concesionaria;
USE concesionaria;

CREATE TABLE concesionario (
  codigo_revision VARCHAR(10) NOT NULL PRIMARY KEY,
  cambio_filtro CHAR(2),
  cambio_aceite CHAR(2),
  cambio_frenos CHAR(2)
);

CREATE TABLE cliente(
  codigo_cliente VARCHAR(10) NOT NULL PRIMARY KEY,
  telefono_cliente CHAR(10),
  nombre_cliente VARCHAR (30) NOT NULL,
  direccion_cliente VARCHAR (50),
  ciudad_cliente VARCHAR (20),
  nif_cliente INT 
);

CREATE TABLE coche (
  matricula VARCHAR(6) PRIMARY KEY,
  marca_coche VARCHAR(20),
  color_coche VARCHAR(20),
  modelo_coche VARCHAR(20),
  precio_coche INT UNSIGNED,
  );
  
codigo_cliente1 VARCHAR(10),
/*referencia a donde es primaria*/
FOREIGN KEY(codigo_cliente) REFERENCES cliente(codigo_cliente)
);
/*tabla intermedia*/
CREATE TABLE concesionario_coche(
  codigo_revision1 VARCHAR(10),
  matricula1 VARCHAR(6),
  FOREIGN KEY(codigo_revision1) REFERENCES concesionario(codigo_revision),  
FOREIGN KEY(matricula1) REFERENCES coche(matricula)
);
