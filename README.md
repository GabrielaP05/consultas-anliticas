# consultas-anliticas
INSERT INTO Categoría (id, nombre)
VALUES
    (1, 'Electrónicos'),
    (2, 'Ropa'),
    (3, 'Hogar'),
    (4, 'Deportes'),
    (5, 'Juguetes');

# tabla Productos
INSERT INTO Producto (id, nombre, marca, categoria_id, precio_unitario)
VALUES
    (1, 'Televisor', 'Sony', 1, 1000),
    (2, 'Laptop', 'HP', 1, 800),
    (3, 'Camisa', 'Zara', 2, 50),
    (4, 'Pantalón', 'Levi''s', 2, 70),
    (5, 'Sartén', 'T-fal', 3, 30),
    (6, 'Toalla', 'Cannon', 3, 20),
    (7, 'Pelota', 'Nike', 4, 15),
    (8, 'Raqueta', 'Wilson', 4, 50),
    (9, 'Muñeca', 'Barbie', 5, 25),
    (10, 'Carro', 'Hot Wheels', 5, 10);

  #Obtener el precio mínimo, precio máximo y precio promedio de todos los productos
SELECT
    MIN(precio_unitario) AS precio_minimo,
    MAX(precio_unitario) AS precio_maximo,
    AVG(precio_unitario) AS precio_promedio
FROM Producto;

#Calcula la cantidad total de productos en stock por sucursal
SELECT
    sucursal_id,
    SUM(cantidad) AS cantidad_total
FROM Stocks
GROUP BY sucursal_id;

#Obtiene el total de ventas por cliente
SELECT
    Cliente.nombre,
    SUM(Items.monto_venta) AS total_ventas
FROM Orden
JOIN Cliente ON Orden.cliente_id = Cliente.id
JOIN Items ON Orden.id = Items.orden_id
GROUP BY Cliente.id;




