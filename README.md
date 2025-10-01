# 👟 Tienda Zapatillas - Base de Datos 🛍️

Este proyecto contiene la base de datos para una tienda de zapatillas. Aquí están los scripts y archivos necesarios para crear y manejar la base de datos `tienda_zapatillas`. ⚙️💾

## 📦 Contenido

- 🗂️ Scripts para crear tablas y relaciones.
- 🔍 Consultas básicas para manipular los datos.
- 📥 Instrucciones para importar la base de datos.

## 🛠️ Tecnologías

- 🐬 MySQL / MariaDB (o el gestor que uses)
- 💻 SQL

## 🚀 Instalación

1. Clona este repositorio:

```bash
git clone https://github.com/MOLINA46/Tienda_Zapatillas-BD.git

CREATE TABLES

CREATE TABLE clientes (
  id_cliente INT PRIMARY KEY,
  nombre VARCHAR(100),
  edad INT,
  sexo ENUM('M', 'F'),
  ciudad VARCHAR(100)
);

CREATE TABLE fechas (
  fecha DATE PRIMARY KEY,
  año INT,
  mes INT,
  dia INT,
  trimestre VARCHAR(10),
  dia_semana VARCHAR(15)
);

CREATE TABLE geolocalizacion (
  id_ubicacion INT PRIMARY KEY,
  nombre_lugar VARCHAR(100),
  tipo_lugar ENUM('Tienda', 'Cliente', 'Almacen'),
  direccion VARCHAR(150),
  barrio VARCHAR(100),
  ciudad VARCHAR(100),
  latitud DECIMAL(10,6),
  longitud DECIMAL(10,6)
);

CREATE TABLE productos (
  id_producto INT PRIMARY KEY,
  nombre_producto VARCHAR(100),
  tipo VARCHAR(50),
  marca VARCHAR(50),
  talla INT,
  color VARCHAR(30),
  precio DECIMAL(10,2)
);

CREATE TABLE tiendas (
  id_tienda INT PRIMARY KEY,
  nombre_tienda VARCHAR(100),
  barrio VARCHAR(100),
  ciudad VARCHAR(100),
  id_ubicacion INT
);

CREATE TABLE ventas (
  id_venta INT PRIMARY KEY,
  id_cliente INT,
  id_producto INT,
  id_tienda INT,
  fecha DATE,
  cantidad INT,
  precio_unitario DECIMAL(10,2),
  total_venta DECIMAL(10,2)
);

INSERTAR DATOS/REGISTROS

-- Insertar en clientes
INSERT INTO clientes (id_cliente, nombre, edad, sexo, ciudad) VALUES
(1, 'Juan Pérez', 30, 'M', 'Bogotá'),
(2, 'María Gómez', 25, 'F', 'Medellín');

-- Insertar en fechas
INSERT INTO fechas (fecha, año, mes, dia, trimestre, dia_semana) VALUES
('2025-09-30', 2025, 9, 30, 'Q3', 'Martes'),
('2025-10-01', 2025, 10, 1, 'Q4', 'Miércoles');

-- Insertar en geolocalizacion
INSERT INTO geolocalizacion (id_ubicacion, nombre_lugar, tipo_lugar, direccion, barrio, ciudad, latitud, longitud) VALUES
(1, 'Tienda Centro', 'Tienda', 'Calle 123 #45-67', 'Centro', 'Bogotá', 4.60971, -74.08175),
(2, 'Casa Juan', 'Cliente', 'Calle 10 #20-15', 'Laureles', 'Medellín', 6.2442, -75.5812);

-- Insertar en productos
INSERT INTO productos (id_producto, nombre_producto, tipo, marca, talla, color, precio) VALUES
(1, 'Zapatilla Air Max', 'Deportiva', 'Nike', 42, 'Rojo', 150.00),
(2, 'Zapatilla Runner', 'Casual', 'Adidas', 40, 'Negro', 120.00);

-- Insertar en tiendas
INSERT INTO tiendas (id_tienda, nombre_tienda, barrio, ciudad, id_ubicacion) VALUES
(1, 'Tienda Centro', 'Centro', 'Bogotá', 1),
(2, 'Sucursal Norte', 'Norte', 'Medellín', 3);

-- Insertar en ventas
INSERT INTO ventas (id_venta, id_cliente, id_producto, id_tienda, fecha, cantidad, precio_unitario, total_venta) VALUES
(1, 1, 1, 1, '2025-09-30', 2, 150.00, 300.00),
(2, 2, 2, 2, '2025-10-01', 1, 120.00, 120.00);
