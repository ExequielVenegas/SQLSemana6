# Proyecto Semana 6 – Implementación de Modelo Relacional (Consultorio Médico)

## 📌 Descripción  
Este proyecto corresponde a la actividad de la **Semana 6** de la asignatura de **Modelamiento de Bases de Datos**.  
El objetivo es implementar en Oracle un modelo relacional para gestionar un **consultorio médico municipal**, incluyendo pacientes, médicos, recetas, medicamentos y pagos.  

---
## 📂 Estructura del script  

1. **Limpieza previa**  
   - Se eliminan todas las tablas en caso de existir (`DROP TABLE ... CASCADE CONSTRAINTS`).  

2. **Creación de tablas (Caso 1)**  
   - Jerarquía de localización:  
     - `REGION → CIUDAD → COMUNA → PACIENTE`.  
   - Entidades principales:  
     - `PACIENTE`, `MEDICO`, `DIGITADOR`, `RECETA`, `MEDICAMENTO`, `PAGO`, `ESPECIALIDAD`.  
   - Restricciones:  
     - `DIGITO_VERIFICADOR` validado con `CHECK` (`0-9` o `K`).  
     - Teléfono de médicos único.  
     - `COMUNA` con `IDENTITY` iniciando en 1101.  
     - `ESPECIALIDAD` con `IDENTITY` autoincremental.  
     - Relaciones con claves primarias y foráneas.  

3. **Modificaciones posteriores (Caso 2)**  
   - Agregar `precio_unitario` en `MEDICAMENTO` con rango entre 1.000 y 2.000.000.  
   - Restringir `PAGO.metodo_pago` a `('EFECTIVO','TARJETA','TRANSFERENCIA')`.  
   - Eliminar columna `edad` en `PACIENTE` y reemplazar por `fecha_nacimiento`.  

---

## ▶️ Ejecución  
1. Conectarse a la base de datos como usuario `PRY2204_S6`.  
2. Abrir `script_semana6.sql` en Oracle SQL Developer.  
3. Ejecutar el script (F5 o botón *Run Script*).  
4. Verificar la creación de las tablas con:  

```sql
SELECT table_name FROM user_tables;
