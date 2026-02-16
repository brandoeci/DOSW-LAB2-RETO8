README - Sistema de Gestión de Zoológico
Descripción del Proyecto
Sistema de gestión para un zoológico que permite administrar animales, cuidadores, visitantes y sus interacciones. Implementa patrones de diseño Strategy para el manejo de diferentes estrategias de alimentación.

Arquitectura del Sistema
Patrón de Diseño: Strategy
El sistema utiliza el patrón Strategy para manejar diferentes estrategias de alimentación de animales.

Estructura de Clases
1. Clase Animal (Abstracta)
Atributos:

nombre: string(50) - Nombre del animal
edad: int(50) - Edad del animal
peso: int(50) - Peso del animal en kg
dieta: string(50) - Tipo de dieta del animal
altura: int(50) - Altura del animal
alimentoPreferido: int(50) - Alimento favorito
habitat: string(50) - Hábitat natural del animal

Métodos:

+ sonidoCaracteristico() - Emite el sonido característico del animal
+ gettersSetters - Métodos de acceso a atributos

Relaciones:

Hereda a: Ave, Mamifero, Reptil
Asociación con Cuidador (muchos a muchos)
Asociación con Visitante (muchos a muchos)


2. Clase Cuidador
Atributos:

nombre: string(50) - Nombre del cuidador
edad: int(50) - Edad del cuidador
especialidad: string(50) - Especialidad (aves, mamíferos, reptiles)

Métodos:

+ bañar() - Método para bañar a los animales
+ alimentar() - Delega la alimentación a AlimentacionStrategy

Relaciones:

Asociación con Animal (muchos a muchos) - Un cuidador puede cuidar varios animales
Usa AlimentacionStrategy (interfaz) - Patrón Strategy


3. Interface AlimentacionStrategy
Tipo: Interface (Patrón Strategy)
Métodos:

+ alimentar() - Método abstracto para estrategia de alimentación

Implementaciones:

AlimentacionCarnivora
AlimentacionHerbivora

Propósito: Permite cambiar dinámicamente la estrategia de alimentación según el tipo de animal.

4. Clases de Estrategia de Alimentación
AlimentacionCarnivora

Implementa AlimentacionStrategy
+ alimentar() - Estrategia específica para carnívoros

AlimentacionHerbivora

Implementa AlimentacionStrategy
+ alimentar() - Estrategia específica para herbívoros


5. Clase Visitante
Atributos:

nombre: string(50) - Nombre del visitante
edad: int(2) - Edad del visitante

Relaciones:

Asociación con Animal (muchos a muchos) - Un visitante puede observar varios animales


6. Clases Hijas de Animal
Ave

Hereda de Animal
Método: + TipoAve - Identifica el tipo de ave

Mamifero

Hereda de Animal
Atributos adicionales:

color: string(50) - Color del pelaje
pelaje: string(50) - Tipo de pelaje



Reptil

Hereda de Animal
Atributos adicionales:

piel - Tipo de piel




Diagrama de Relaciones
Relaciones Clave:

Herencia:

Animal hereda a Ave, Mamifero, Reptil


Asociaciones:

Animal asociado con Cuidador (muchos a muchos)
Animal asociado con Visitante (muchos a muchos)


Patrón Strategy:

Cuidador usa AlimentacionStrategy
AlimentacionStrategy implementado por AlimentacionCarnivora y AlimentacionHerbivora




Patrones de Diseño Implementados
Strategy Pattern
Problema que resuelve:
Diferentes tipos de animales requieren diferentes estrategias de alimentación.
Solución:

La interfaz AlimentacionStrategy define el contrato
Implementaciones concretas (AlimentacionCarnivora, AlimentacionHerbivora) proporcionan comportamientos específicos
Cuidador puede cambiar la estrategia dinámicamente según el animal

Ventajas:

Separa el algoritmo de alimentación de la lógica del cuidador
Fácil agregar nuevas estrategias (ej: AlimentacionOmnivora)
Cumple principio Open/Closed (abierto a extensión, cerrado a modificación)


Casos de Uso
1. Alimentar un Animal
javaCuidador cuidador = new Cuidador("Juan", 30, "Mamíferos");
Animal leon = new Mamifero("León", 5, 190, "Carnívoro", ...);

cuidador.setEstrategia(new AlimentacionCarnivora());
cuidador.alimentar(leon);
2. Cambiar Estrategia Dinámicamente
cuidador.setEstrategia(new AlimentacionHerbivora());
Animal elefante = new Mamifero("Elefante", 10, 5000, "Herbívoro", ...);
cuidador.alimentar(elefante);
3. Registrar Visita
javaVisitante visitante = new Visitante("María", 25);
visitante.observar(leon);

Cardinalidades

Animal - Cuidador: Muchos a Muchos (un animal puede tener varios cuidadores, un cuidador puede cuidar varios animales)
Animal - Visitante: Muchos a Muchos (un animal puede ser visitado por varios visitantes, un visitante puede ver varios animales)
Cuidador - AlimentacionStrategy: Uno a Uno (un cuidador usa una estrategia a la vez, pero puede cambiarla)


Tecnologías Sugeridas

Lenguaje: Java
Build Tool: Maven / Gradle
Testing: JUnit
UML: PlantUML / Draw.io


Extensibilidad Futura
Posibles Mejoras:

Nuevas Estrategias:

AlimentacionOmnivora
AlimentacionInsectivora


Nuevos Tipos de Animales:

Anfibio
Pez


Funcionalidades Adicionales:

Sistema de salud para animales
Gestión de horarios de alimentación
Registro de actividades de visitantes
Sistema de reproducción de animales


Otros Patrones:

Observer: Notificar cuando un animal necesita atención
Factory: Crear animales según tipo
Singleton: Gestión única del zoológico




Roles y Responsabilidades
Animal:

Mantener información personal
Emitir sonido característico
Ser observable por visitantes

Cuidador:

Cuidar animales (bañar, alimentar)
Usar estrategias de alimentación apropiadas
Gestionar múltiples animales

Visitante:

Observar animales
Registrar visitas

AlimentacionStrategy:

Definir comportamiento de alimentación
Permitir intercambio de estrategias


Principios SOLID Aplicados

S (Single Responsibility): Cada clase tiene una responsabilidad única
O (Open/Closed): Abierto a extensión (nuevas estrategias) sin modificar código existente
L (Liskov Substitution): Las estrategias son intercambiables
I (Interface Segregation): Interface simple y específica para alimentación
D (Dependency Inversion): Cuidador depende de abstracción (AlimentacionStrategy), no de implementaciones concretas


<img width="1071" height="512" alt="image" src="https://github.com/user-attachments/assets/690e4d8b-0731-476a-a93f-cebcac5fa54b" />






Versión: 1.0
Fecha: Febrero 2026
Autor: Hildebrando
