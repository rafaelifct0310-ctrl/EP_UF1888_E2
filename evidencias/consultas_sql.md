# Consultas SQL

## Consulta 1: Ventas con cliente y fecha

```sql

SELECT
    so.name AS pedido,
    rp.name AS cliente,
    so.date_order AS fecha,
    so.amount_total AS importe_total
 FROM sale_order so
 JOIN res_partner rp ON so.partner_id = rp.id
 ORDER BY so.date_order DESC;
```
Esta consulta muestra los pedidos de venta, el cliente asociado, la fecha del pedido y el importe total.

# Consulta 2: Suma del importe vendido por cliente

```sql
SELECT 
    rp.name AS cliente,
    SUM(so.amount_total) AS total_vendido
FROM sale_order so
JOIN res_partner rp ON so.partner_id = rp.id
GROUP BY rp.name
ORDER BY total_vendido DESC;
```

# Consulta 3: productos más vendidos según cantidad

```sql
SELECT
    pt.name AS producto,
    SUM(sol.product_uom_qty) AS cantidad_total_vendida
FROM sale_order_line sol
JOIN product_product pp ON sol.product_id = pp.id
JOIN product_template pt ON pp.product_tmpl_id = pt.id
GROUP BY pt.name
ORDER BY cantidad_total_vendida DESC;
```

# Consulta 4: pedidos realizados en un intervalo de fechas

```sql
SELECT 
    so.name AS pedido,
    rp.name AS cliente,
    so.date_order AS fecha,
    so.amount_total AS importe_total
FROM sale_order so
JOIN res_partner rp ON so.partner_id = rp.id
WHERE so.date_order BETWEEN '2026-03-01' AND '2026-03-31'
ORDER BY so.date_order ASC;
```

