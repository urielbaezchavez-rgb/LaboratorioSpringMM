# Respuestas del Laboratorio - Spring Many-to-Many

## Paso 1: Análisis del modelo Department
**Pregunta:** ¿Cómo afectará JPA a la base de datos? ¿Qué tabla creará y qué columnas tendrá?

**Respuesta:** Al utilizar las anotaciones `@ManyToMany` y `@JoinTable` en el modelo `Department`, JPA creará automáticamente una tabla de unión (intermedia) llamada `producto_deparments`. Esta tabla no contiene atributos propios, sino dos columnas que funcionan como llaves foráneas: `product_id` (que hace referencia al ID del producto) y `deparments_id` (que hace referencia al ID del departamento/categoría).