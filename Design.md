DOCUMENTACIÓN DE DISEÑO: SISTEMAS DE GESTIÓN DE RESERVAS

1. Modelos de Casos de Uso (Diagrama 1)

El objetivo es definir el alcance y los límites del sistema.

Actores: Socio (Usuario) y Administrador (Gestión).
Decisiones Clave: Se utilizó <<Include>> para centralizar la seguridad y <<extend>> para la Lista de Espera, asegurando que esta última sea una funcionalidad modular que no bloquee el flujo principal de reserva.


2. Modelo de Interacción (Diagramas 2 y 3)

El objetivo es detallar el paso de mensajes entre objetos.

Secuencia: Muestra el flujo temporal desde que el Socio pulsa "Confirmar". El uso del fragmento alt es vital para gestionar la excepción  de "Aforo Completo".

Comunicación: Enfatiza la topología de red, mostrando que el GestorReservas centraliza la lógica, evitando que la InterfazWeb toque directamente la BaseDatos.

3. Modelo de Procesos/Actividades (Diagrama 4).

El objetivo, controlar la integridad del objeto Reserva.

Ciclo Vida: La reserva pasa por estados que permiten trazabilidad total.

Control de Asistencia: Los estados Realizada y No Presentado permiten al Gym analizar el uso de sus recursos y aplicar penalizaciones si es necesario.

4. Modelo de Comportamiento de Estado (Diagrama 5).

El objetivo de la integridad del objeto Reserva.

Ciclo de Vida: La reserva pasa por estados que permiten trazabilidad total.

Control de Asistencia: Los estados Realizada y No Presetado permiten al gimnasio analizar el uso de sus recursos y aplicar penalizaciones si es necesario.