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

Ejercicio 2.

```mermaid

sequenceDiagram
    autonumber
    actor Socio
    participant IW as :InterfazWeb
    participant GR as :GestorReservas
    participant BD as :BaseDatos

    Socio->>IW: Pulsar "Confirmar Reserva"
    IW->>GR: enviarPeticion(idSocio, idClase)
    GR->>BD: consultarDisponibilidad(idClase)
    BD-->>GR: cupoDisponible / cupoLleno

    alt Hay hueco disponible
        GR->>BD: registrarReserva(idSocio, idClase)
        BD-->>GR: reservaConfirmada
        GR-->>IW: confirmacionExitosa
        IW-->>Socio: Mostrar "Reserva realizada con éxito"
    else Clase llena
        GR-->>IW: errorCupoAgotado
        IW-->>Socio: Mostrar "Clase llena. ¿Desea lista de espera?"
    end

```

Ejercicio 3.

```mermaid

graph LR
    %% Objetos (Nodos)
    S((:Socio))
    IW[":InterfazWeb"]
    GR[":GestorReservas"]
    BD[(":BaseDatos")]

    %% Enlaces y Mensajes
    S -- "1. pulsarConfirmar()" --> IW
    IW -- "2. enviarPeticion()" --> GR
    GR -- "3. consultarDisponibilidad()" --> BD
    BD -. "4. responderEstado()" .-> GR
    
    %% Flujo de éxito (Numeración decimal)
    GR -- "5.1 [si hay hueco] registrarReserva()" --> BD
    BD -. "5.2 confirmarRegistro()" .-> GR
    GR -. "5.3 respuestaExito()" .-> IW
    IW -. "5.4 mostrarMensaje()" .-> S

    %% Flujo alternativo
    GR -. "6.1 [si está llena] informarError()" .-> IW

```