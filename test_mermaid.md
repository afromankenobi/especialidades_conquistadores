# Test de Diagramas Mermaid.js

Este archivo es para probar que los diagramas Mermaid.js se renderizan correctamente.

## Diagrama de Flujo Simple

```mermaid
graph TD
    A[Inicio] --> B{¿Funciona?}
    B -->|Sí| C[¡Excelente!]
    B -->|No| D[Revisar código]
    D --> A
    style A fill:#90EE90
    style C fill:#FFD700
```

## Diagrama de Secuencia

```mermaid
sequenceDiagram
    participant Usuario
    participant Navegador
    participant Jekyll
    participant Mermaid
    
    Usuario->>Jekyll: Escribe ```mermaid
    Jekyll->>Navegador: Genera HTML con <pre><code>
    Navegador->>Mermaid: JavaScript convierte a <div>
    Mermaid->>Usuario: Muestra diagrama renderizado
```

## Diagrama de Partes de una Hoja (del archivo arboles.md)

```mermaid
graph TB
    subgraph LIMBO["<b>LIMBO (Lámina foliar)</b><br/>Parte plana y ancha<br/>Donde ocurre la fotosíntesis"]
        Apice["<b>Ápice</b><br/>Punta de la hoja"]
        NervCentral["<b>Nervadura Central</b><br/>Venas que transportan<br/>agua y nutrientes"]
        NervSec["<b>Nervaduras Secundarias</b><br/>Ramificaciones laterales"]

        Apice --- NervCentral
        NervCentral --- NervSec
    end

    LIMBO ---|conecta| Peciolo["<b>PECÍOLO</b><br/>Tallo que une la hoja al tallo<br/>Permite orientación hacia la luz"]

    Peciolo --- Estipulas["<b>ESTÍPULAS</b><br/>Apéndices pequeños en la base<br/>(no todas las hojas los tienen)"]

    Estipulas --- Axila["<b>AXILA FOLIAR</b><br/>Ángulo entre pecíolo y tallo<br/>Donde pueden crecer yemas"]

    Axila --- Tallo["<b>TALLO PRINCIPAL</b>"]

    style LIMBO fill:#90EE90
    style Peciolo fill:#F0E68C
    style Estipulas fill:#FFB6C1
    style Axila fill:#E0E0E0
    style Tallo fill:#8B4513,color:#fff
```

## Instrucciones

Si ves diagramas renderizados arriba (no código), ¡la solución funciona!

Si ves bloques de código con sintaxis mermaid sin renderizar:
1. Verifica que estás viendo esto a través de Jekyll (no directamente en GitHub)
2. Revisa la consola del navegador (F12) para errores
3. Consulta [docs/MERMAID_FIX.md](docs/MERMAID_FIX.md) para más ayuda
