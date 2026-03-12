# Gesti-n_del_Sistema_-GymMaster-
El gimnasio "GymMaster" quiere digitalizar un proceso crítico: La gestión de Clases Colectivas con reserva previa. Como analista de software, debes entregar la documentación técnica de este módulo utilizando UML.

Ejercicio 1.

```mermaid
useCaseDiagram
    actor "Socio" as S
    actor "Administrador" as A

    package "Sistema de Gestión de Gimnasio" {
        usecase "Identificarse (Login)" as UC_Login
        usecase "Reservar Clase" as UC_Reservar
        usecase "Apuntarse en Lista de Espera" as UC_Espera
        usecase "Dar de alta nuevas clases" as UC_Alta
        usecase "Cancelar sesiones" as UC_Cancelar
    }

    %% Relaciones del Socio
    S --> UC_Reservar
    
    %% Relaciones del Administrador
    A --> UC_Alta
    A --> UC_Cancelar

    %% Relaciones Include (Obligatorias)
    UC_Reservar ..> UC_Login : <<include>>
    UC_Alta ..> UC_Login : <<include>>
    UC_Cancelar ..> UC_Login : <<include>>

    %% Relación Extend (Opcional bajo condición)
    UC_Espera ..> UC_Reservar : <<extend>>

```