# Gesti-n_del_Sistema_-GymMaster-

El gimnasio "GymMaster" quiere digitalizar un proceso crítico: La gestión de Clases Colectivas con reserva previa. 
Como analista de software, debes entregar la documentación técnica de este módulo utilizando UML.

Ejercicio 1.

```mermaid

graph TD
    subgraph "Sistema de Gestión de Gimnasio"
        UC_Login(["Identificarse (Login)"])
        UC_Reservar(["Reservar Clase"])
        UC_Espera(["Apuntarse en Lista de Espera"])
        UC_Alta(["Dar de alta nuevas clases"])
        UC_Cancelar(["Cancelar sesiones"])
    end

    %% Actores
    Socio((Socio))
    Admin((Administrador))

    %% Conexiones de Actores
    Socio --- UC_Reservar
    Admin --- UC_Alta
    Admin --- UC_Cancelar

    %% Relaciones Include (Flecha discontinua hacia el incluido)
    UC_Reservar -.->|"<<include>>"| UC_Login
    UC_Alta -.->|"<<include>>"| UC_Login
    UC_Cancelar -.->|"<<include>>"| UC_Login

    %% Relación Extend (Flecha discontinua desde la extensión al base)
    UC_Espera -.->|"<<extend>>"| UC_Reservar

```