# ADAT-3-Proyecto

## API usando SpringBoot

### 1. Idea

Voy a hacer una API REST de gestión de viajes en grupo (uno de los ejemplos).

**Idea:** Aplicación de gestión de viajes en grupo

#### Tablas involucradas:
- **Tabla 1:** Usuarios
- **Tabla 2:** Viajes
- **Tabla 3:** Destinos

---

### 2. Tablas

#### Tabla Usuarios
| Campo        | Tipo   | Restricciones                                   |
|--------------|--------|------------------------------------------------|
| **id**       | String | UNIQUE, PRIMARY KEY, 10 caracteres            |
| **name**     | String | NOT NULL, Máximo 20 caracteres                 |
| **surname**  | String | NOT NULL, Máximo 50 caracteres                 |
| **birthdate**| Date   | NOT NULL                                       |
| **dni**      | String | NOT NULL, 9 caracteres                        |

**Notas:**
- El `id` se crea usando las tres primeras letras del nombre, y de los apellidos más un número aleatorio al final.
- El `dni` tiene que seguir las restricciones que aseguran que sea correcto (AKA que la letra sea la correcta segun los numeros).

---

#### Tabla Viajes
| Campo              | Tipo         | Restricciones                                    |
|--------------------|--------------|-------------------------------------------------|
| **id**             | String       | UNIQUE, PRIMARY KEY, 10 caracteres             |
| **destination**    | Destino      | SECONDARY KEY                                   |
| **date**           | Date         |                                                 |
| **method_of_travel** | String      | ENUM: Car, Bus, Train, Plane, Boat             |
| **participants**   | Usuario      | SECONDARY KEY                                   |

**Notas:**
- El `id` se crea usando las tres primeras letras del destino más las tres primeras letras del método de viaje. Después se añaden cuatro caracteres aleatorios.

---

#### Tabla Destinos
| Campo      | Tipo   | Restricciones                                   |
|------------|--------|------------------------------------------------|
| **id**     | String | UNIQUE, PRIMARY KEY, 10 caracteres            |
| **name**   | String | NOT NULL, Máximo 20 caracteres                 |
| **country**| String | NOT NULL, Máximo 20 caracteres                 |

**Notas:**
- El `id` se forma con las tres primeras letras del nombre del destino y del país más cuatro caracteres aleatorios.

###3. Diagrama entidad-relación

  ![Diagrama ClaseEntidad drawio](https://github.com/user-attachments/assets/1ab8161d-8bd8-4c0c-b30c-0b3065812e36)

