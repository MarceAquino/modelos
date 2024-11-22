# 🚛 Gestión de Flotas de Transporte 🚗🚌

Un sistema para gestionar una flota de transporte que incluye **camiones**, **buses** y **autos**. Este sistema permite:  
- 📆 **Gestionar alquileres**: Calcula costos según el tipo de vehículo y días de alquiler.  
- 🛠️ **Realizar mantenimientos**: Controla la disponibilidad de los vehículos.  
- 📊 **Consultar estadísticas**: Proporciona datos sobre el uso de los vehículos.  
- 💾 **Persistencia de datos**: Guarda y carga información en archivos binarios.  

## 📝 Requisitos del Sistema

### 🛠️ Capa Modelo  
#### Clase Abstracta: `Vehículo`  
**Atributos:**  
- `int id`: Identificador único incremental.  
- `String placa`: Matrícula del vehículo.  
- `double costoPorDia`: Costo diario de alquiler.  
- `boolean enMantenimiento`: Disponibilidad del vehículo.  

**Métodos abstractos:**  
- `double calcularCostoFinal(int dias)`: Calcula el costo total en función del tipo de vehículo.  
- `void realizarMantenimiento()`: Marca el vehículo como en mantenimiento.  

**Métodos generales:**  
- `Optional<String> verificarDisponibilidad()`: Devuelve la disponibilidad del vehículo.  

#### Subclases:
- **`Camión`**: Incrementa el costo por carga adicional.  
- **`Bus`**: Incrementa el costo según la cantidad de pasajeros.  
- **`Auto`**: Incrementa el costo si se alquila para viajes largos.  

---

#### Clase: `Alquiler`  
**Atributos:**  
- `String cliente`: Nombre del cliente.  
- `int idVehiculo`: ID del vehículo alquilado.  
- `int dias`: Días de alquiler.  

---

#### Clase: `GestorFlota`  
**Atributos:**  
- `List<Vehiculo> flota`: Lista de vehículos registrados.  

**Métodos:**  
- `boolean registrarVehiculo(Vehiculo vehiculo)`: Agrega un vehículo al sistema.  
- `Optional<Vehiculo> buscarPorId(int id)`: Busca un vehículo por su ID.  
- `List<Vehiculo> consultarDisponibles()`: Devuelve una lista de vehículos disponibles.  

---

#### Clase: `GestorAlquileres`  
**Atributos:**  
- `List<Alquiler> alquileres`: Lista de alquileres realizados.  

**Métodos:**  
- `boolean realizarAlquiler(String cliente, int idVehiculo, int dias)`: Procesa el alquiler de un vehículo.  
- `Map<String, Long> estadisticasUsoPorTipo()`: Genera estadísticas por tipo de vehículo.  

---

#### Clase: `Persistencia`  
**Métodos:**  
- Guardar y cargar datos de vehículos y alquileres en archivos binarios.  

---

## ✅ Pruebas Implementadas  
- ✔️ Registrar múltiples vehículos y verificar identificadores únicos.  
- ✔️ Realizar mantenimientos y validar su impacto en la disponibilidad.  
- ✔️ Alquilar vehículos, simular el límite de capacidad y generar estadísticas.  
- ✔️ Guardar y cargar datos desde archivos binarios.  

---

## 🛠️ Tecnologías Utilizadas  
- Lenguaje: **Java 22** ☕  
- Persistencia: Archivos binarios 📂  
- Programación Funcional: Uso de `Optional` y Streams 🚀  

---

## 📂 Estructura del Proyecto  
```plaintext
src/
├── modelo/
│   ├── Vehiculo.java
│   ├── Camion.java
│   ├── Bus.java
│   ├── Auto.java
│   ├── Alquiler.java
├── gestor/
│   ├── GestorFlota.java
│   ├── GestorAlquileres.java
├── persistencia/
│   ├── Persistencia.java
├── tests/
│   ├── Pruebas.java
📊 Resultados Esperados
Registro exitoso de vehículos.
Validación del mantenimiento y su impacto en la disponibilidad.
Estadísticas claras del uso de la flota.
Datos persistentes almacenados correctamente.
