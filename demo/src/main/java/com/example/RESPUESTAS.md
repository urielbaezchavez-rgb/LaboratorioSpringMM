# Respuestas del Laboratorio - Spring Many-to-Many

## Paso 1: Análisis del modelo Department
**Pregunta:** ¿Cómo afectará JPA a la base de datos? ¿Qué tabla creará y qué columnas tendrá?

**Respuesta:** Al utilizar las anotaciones `@ManyToMany` y `@JoinTable` en el modelo `Department`, JPA creará automáticamente una tabla de unión (intermedia) llamada `producto_deparments`. Esta tabla no contiene atributos propios, sino dos columnas que funcionan como llaves foráneas: `product_id` (que hace referencia al ID del producto) y `deparments_id` (que hace referencia al ID del departamento/categoría).

## Paso 2: Análisis de la relación en Producto y @JsonIgnore

**Pregunta:** Investiga qué significa la anotación `@JsonIgnore` y explica por qué crees que se utiliza en `Producto`.

**Respuesta:** 
- **Significado de `@JsonIgnore`:** Es una anotación de la librería Jackson que le indica al serializador que ignore esa propiedad/campo al convertir el objeto Java a formato JSON (y viceversa).
- **Por qué se utiliza en `Producto`:** Al tener una relación bidireccional `@ManyToMany` entre `Department` y `Producto`, si no se coloca `@JsonIgnore`, Jackson entraría en un bucle infinito de serialización (un `Department` serializa sus `productos`, cada `Producto` serializa sus `deparments`, y así sucesivamente hasta provocar un error `StackOverflowError`). `@JsonIgnore` corta este ciclo en la clase `Producto`.