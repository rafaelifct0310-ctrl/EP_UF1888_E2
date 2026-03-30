# Identificación tablas origen

`res_partner`
Aquí se almacenan los: clientes, proveedores, emporesas, personas.

`sale_order`
Aquí se almacena la cabecera del pedido:

- cliente
- fecha
- estado
- importe total
- referencia pedido

`sale_order_line`
Aquí se almacena el detalle
- producto
- cantidad
- precio unitario
- subtotal
- pedido al que pertence

## 4. Productos
Tablas/modelos : product_product y product_template
Uso: contiene la información de los productos comercializados.

## Relación entre tablas
- sale_order.partner_id -> res_partner.id
- sale_order_line.order.id -> sale_order.id
- sale_order_line.product_id -> product_product.id
- product_product.product_tmpl.id -> product_template.id



