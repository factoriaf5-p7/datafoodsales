# DATA FOOD SALES

## Intro

Vamos a practicar con la carga de información dentro de una bd de mySQL. Partiremos de un fichero excel con una lista de ventas de productos por ciudades. El formato de la hoja contiene los siguientes campos: ID, Date, Region, City, Category, Product, Qty, UnitPrice.

Queremos una base de datos que contenga las siguientes tablas y campos:
- **city**:
  - `id` primary key, integer, auto incremental
  - `name` varchar(45) not null unique key
  - `region` enum('East','West') not null
- **product**:
  - `id` primary key, integer, auto incremental
  - `name` varchar(45) not null unique key
  - `unit_price` integer not null
  - `category` enum('Bars', 'Snacks', 'Cookies', 'Crackers') not null
- **sale**:
  - `id` primary key, integer
  - `product_id` int not null foreign key (`id` tabla `product`)
  - `sale_date` Date not null
  - `city_id` int not null foreign key (`id` tabla `city`)
  - `qty` integer default (0)

## Iteraciones

1. Exporta la hoja de excel a un formato de datos admitido por mySQL (csv o json)
2. Crea la bbdd con el nombre data_food
3. Importa los datos en una tabla dentro de tu esquema de bbdd
4. Crea las tablas con los requerimientos que tienes en la introducción
5. Carga los datos en cada tabla utilizando la estructura:
```sql
INSERT INTO target_table (FIELDS) SELECT FIELDS from origin_table
```
6. Borra la tabla de carga.
7. Realiza las siguientes consultas sobre tus tablas:
   - Lista de products x city con el importe total de venta
   - Lista de importe total de ventas x categoría
   - Lista de importe total de ventas x city
   - Calcula el mes en el que hubo más ventas en la región "East"