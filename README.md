# Base de Datos: Concesionario de Vehículos

## Descripción
Este proyecto define la estructura de una base de datos para gestionar un concesionario de vehículos. Se incluyen entidades como vehículos, clientes, empleados, ventas, servicios de mantenimiento y métodos de pago, estableciendo relaciones entre ellas para asegurar la coherencia y eficiencia en la gestión de los datos.

## Justificación del Diseño
El diseño de la base de datos sigue un modelo relacional donde:
- Se separan las entidades en tablas específicas para evitar redundancias y facilitar la escalabilidad.
- Se definen claves primarias (PK) autoincrementales para asegurar la unicidad de los registros.
- Se utilizan claves foráneas (FK) para establecer relaciones entre entidades y garantizar la integridad referencial.
- Se crean restricciones de unicidad en datos clave como el correo electrónico y el número de empleado para evitar duplicados.

### Modelo Entidad-Relación (ERD)
A continuación, se presentan los diagramas de la base de datos:

### **Diagrama Físico de la Base de Datos**
![Diagrama Físico](diagramamermaid.png)

### **Diagrama UML de la Base de Datos**
![Diagrama UML](diagramalucidchart.png)

## Restricciones y Validaciones
### Claves Primarias (PK)
Cada tabla tiene una clave primaria que la identifica de manera única:
- `VEHICULOS (VIN)`
- `CLIENTES (ClienteID)`
- `EMPLEADOS (EmpleadoID)`
- `VENTAS (VentaID)`
- `DETALLE_VENTAS (DetalleID)`
- `SERVICIOS_MANTENIMIENTO (ServicioID)`
- `TIPOS_COMBUSTIBLE (TipoCombustibleID)`
- `TIPOS_TRANSMISION (TipoTransmisionID)`
- `ESTADOS_VEHICULO (EstadoID)`
- `METODOS_PAGO (MetodoPagoID)`

### Claves Foráneas (FK)
Las claves foráneas aseguran la relación entre las entidades:
- `VEHICULOS` → `TipoCombustibleID` referencia a `TIPOS_COMBUSTIBLE`
- `VEHICULOS` → `TipoTransmisionID` referencia a `TIPOS_TRANSMISION`
- `VEHICULOS` → `EstadoID` referencia a `ESTADOS_VEHICULO`
- `CLIENTES` → `PersonaFisicaID` referencia a `PERSONAS_FISICAS`
- `EMPLEADOS` → `PersonaFisicaID` referencia a `PERSONAS_FISICAS`
- `VENTAS` → `ClienteID` referencia a `CLIENTES`
- `VENTAS` → `EmpleadoID` referencia a `EMPLEADOS`
- `VENTAS` → `MetodoPagoID` referencia a `METODOS_PAGO`
- `DETALLE_VENTAS` → `VentaID` referencia a `VENTAS`
- `DETALLE_VENTAS` → `VIN` referencia a `VEHICULOS`
- `SERVICIOS_MANTENIMIENTO` → `VIN` referencia a `VEHICULOS`
- `SERVICIOS_MANTENIMIENTO` → `ClienteID` referencia a `CLIENTES`
- `SERVICIOS_MANTENIMIENTO` → `TipoServicioID` referencia a `TIPOS_SERVICIO`

### Restricciones de Unicidad
- `CorreoElectronico` en `PERSONAS_FISICAS` es único para evitar registros duplicados.
- `NumeroEmpleado` en `EMPLEADOS` es único para identificar empleados de manera exclusiva.
- `PersonaFisicaID` en `CLIENTES` y `EMPLEADOS` es único para que una persona solo pueda ser cliente o empleado una vez.

## Relaciones UML
Las relaciones entre las entidades están representadas en el diagrama UML, donde se establecen las cardinalidades y restricciones:
- Un `CLIENTE` puede realizar múltiples `VENTAS`.
- Un `EMPLEADO` (vendedor) puede gestionar múltiples `VENTAS`.
- Un `VEHÍCULO` puede estar involucrado en múltiples `DETALLE_VENTAS`.
- Un `VEHÍCULO` puede recibir múltiples `SERVICIOS_MANTENIMIENTO`.
- Un `CLIENTE` puede solicitar (opcionalmente) servicios de mantenimiento.
- Un `TIPO_SERVICIO` clasifica diferentes `SERVICIOS_MANTENIMIENTO`.

## Conclusión
Este diseño de base de datos garantiza la eficiencia en la gestión de un concesionario de vehículos, permitiendo un control estructurado de los datos y asegurando la integridad referencial mediante relaciones bien definidas. 

---

Si necesitas ajustes o explicaciones adicionales, no dudes en preguntar. 🚀