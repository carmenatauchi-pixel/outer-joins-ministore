-- 1. ¿Por qué usaste LEFT JOIN para la Consulta 1 y no INNER JOIN? ¿Qué se perdería si usaras INNER JOIN?
-- Utilicé LEFT JOIN porque la idea era partir de la tabla productos y asegurarme de que aparezcan todos 
-- los productos del catálogo, incluso aquellos que nunca tuvieron una venta.
-- Si hubiera usado un INNER JOIN, solo se mostrarían los productos que tienen una coincidencia en la tabla ventas. 
-- En este caso, se perderían los productos 108 (Hub USB-C 7p) y 109 (Parlante Bluetooth), ya que nunca fueron vendidos 
-- y no tienen registros asociados en la tabla ventas.


-- 2. ¿Por qué usaste RIGHT JOIN para la Consulta 2? ¿Qué tabla está a la izquierda y cuál a la derecha en tu consulta?
-- Utilicé RIGHT JOIN porque en este caso lo importante era conservar todas las ventas registradas, incluso si alguna 
-- hace referencia a un producto que no existe en el catálogo.
-- En mi consulta, la tabla productos está a la izquierda y la tabla ventas está a la derecha. Al usar RIGHT JOIN, 
-- SQL devuelve todos los registros de la tabla ventas, lo que permite identificar fácilmente ventas con productos 
-- inexistentes, como el producto_id = 999.


-- 3. ¿Qué representan los valores NULL en cada resultado? Explicá con un ejemplo concreto de los datos qué significa 
-- que venta_id sea NULL en la Consulta 1 y que producto_id de productos sea NULL en la Consulta 2.
-- Los valores NULL indican que no existe una coincidencia entre las dos tablas.
-- En la Consulta 1, si venta_id aparece como NULL, significa que el producto sí existe en el catálogo, pero nunca 
-- fue vendido. Por ejemplo, los productos 108 y 109 aparecen con NULL en las columnas de ventas porque no tienen 
-- ninguna venta registrada.
-- En la Consulta 2, cuando producto_id de la tabla productos aparece como NULL, significa que sí existe una venta, 
-- pero el producto asociado no está registrado en el catálogo. En este caso ocurre con la venta 10, que tiene el 
-- producto_id = 999 en la tabla ventas, pero ese código no existe en la tabla productos.


-- 4. ¿Cuándo usarías FULL OUTER JOIN en un caso real de negocio?
-- Usaría un FULL OUTER JOIN cuando quisiera hacer una auditoría de datos y validar que la información de dos tablas 
-- sea consistente. Por ejemplo, para identificar al mismo tiempo productos que nunca fueron vendidos y ventas registradas 
-- con productos inexistentes en el catálogo.
-- Me parece especialmente útil cuando se quiere revisar la calidad de la información antes de generar reportes o analizar 
-- indicadores, ya que permite detectar inconsistencias o errores de carga sin dejar fuera ningún registro.




