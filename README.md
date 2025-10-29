# Plantilla Context Engineering

A continuación se presenta una plantilla completa para comenzar con Context Engineering: la disciplina de Context Engineering para asistentes de código de IA para que tengan la información necesaria para realizar el trabajo de principio a fin.
> **Context Engineering is 10x mejor que prompt engineering y 100x mejor que vibe coding.**

## 🚀 Quick Start

```bash
# 1. Clone esta plantilla
git clone https://github.com/elipirela/Context-Engineering-espanol.git
cd Context-Engineering-espanol

# 2. Configura las reglas del proyecto (opcional - plantilla proporcionada)
# Edita CLAUDE.md para agregar las guías específicas de tu proyecto

# 3. Agrega ejemplos (muy recomendado)
# Coloca ejemplos relevantes de código en la carpeta de ejemplos

# 4. Crea tu requerimiento de funcioes iniciales
# Edita INICIO.md utilizando tus requerimientos de funiciones 

# 5. Genera un PRP funcional (Product Requirements Prompt)
# En Claude Code, VSC, Cursor, etc. run:
/generate-prp INICIO.md

# 6. Executar el PRP para implementar tus funciones
# En Claude Code, VSC, Cursor, etc. run:
/execute-prp PRPs/nombre-de-tu-archivo.md
```

## 📚 Tabla de Contenido

- Que es Context Engineering?
- Etructura de plantilla
- Guía paso a paso
- Escribe un archivo de INICIO.md efectivo
- El flujo de trabajo PRP
- Usando Ejemplos efectivos
- Mejores Practicas

## Que es Context Engineering?

Context Engineering representa un cambio de paradigma del prompt engineering tradicional:

### Prompt Engineering vs Context Engineering

**Prompt Engineering:**
- Se centra en la redacción inteligente y la formulación específica.
- Limitado a cómo formulas una tarea
- Como darle una nota adhesiva a alguien

**Context Engineering:**
- Un sistema completo para proporcionar un contexto integral
- Incluye documentación, ejemplos, reglas, patrones y validación.
- Como escribir un guión completo con todos los detalles.

### Por que es importante el Context Engineering

1. **Reduce las fallas de AI**: Las fallas del agente no son fallas del modelo, son fallas del contexto.
2. **Asegura Consistencia**: La IA sigue los patrones y convenciones de tu proyecto
3. **Permite funciones complejas**: La IA puede gestionar implementaciones de varios pasos con el contexto adecuado
4. **Auto-Corrección**: Los bucles de validación permiten que la IA corrija sus propios errores

## Estructura de la Plantilla

```
context-engineering-espanol/
├── .claude/
│   ├── commands/
│   │   ├── generate-prp.md    # Genera PRP completos
│   │   └── execute-prp.md     # Ejecuta PRP para implementar funciones
│   └── settings.local.json    # Permisos de Claude Code
├── PRPs/
│   ├── templates/
│   │   └── prp_base.md        # Plantilla base para PRP
│   └── EXAMPLE_multi_agent_prp.md  # Ejemplo de un PRP completo
├── ejemplos/                 # Ejemplos de codigo (critical!)
├── CLAUDE.md                 # Reglas globales para el asistente de IA
├── INICIO.md                 # Plantilla para solicitudes de funciones
├── INITIAL_EXAMPLE.md        # Ejemplo de solicitud de función
└── README.md                 # Este archivo
```


## Guía paso a paso

### 1. Configura reglas globales (CLAUDE.md)

El archivo `CLAUDE.md` contiene las reglas generales del proyecto que el asistente de IA seguirá en cada conversación. La plantilla incluye:

- **Reconocimiento del Projecto**: Lectura de documentos de planificación, comprobación de tareas
- **Estructura de Codigo**: Límites de tamaño de archivo, organización del módulo
- **Requerimientos de pruebas**: Patrones de pruebas unitarias, expectativas de cobertura
- **Convenciones de estilos**: Preferencias de idioma, reglas de formato
- **Estándares de la Documentación**: Formatos de cadenas de documentación, prácticas de comentarios

**Puedes utilizar la plantilla proporcionada tal como está o personalizarla para tu proyecto..**

### 2. Crea tu requierimiento inicial de funciones

Edita `INICIO.md` para describir que es lo que deseas construir:

```markdown
## FEATURE:
[Describe lo que quieres construir: sé específico sobre la funcionalidad y los requisitos]

## EJEMPLOS:
[Enumere todos los archivos de ejemplo en la carpeta examples/ y explique cómo deben usarse]

## DOCUMENTACION:
[Incluya enlaces a documentación relevante, API o recursos del servidor MCP]

## OTRAS CONSIDERACIONES:
[Mencione problemas, requisitos específicos o cosas que los asistentes de IA suelen pasar por alto.]
```

**Ver `INITIAL_EXAMPLE.md` para un ejemplo completo.**

### 3. Generar el PRP

PRPs (Product Requirements Prompts) son planes de implementación integrales que incluyen:

- Contexto completo y documentación
- Pasos de implementación con validación
- Patrones de manejo de errores
- Requisitos de la prueba

Son similares a los PRD (Documentos de requisitos del producto) pero están diseñados más específicamente para instruir a un asistente de codificación de IA.

Run en Claude Code:
```bash
/generate-prp INICIO.md
```

**Note:** Los comandos slash / son comandos personalizados definidos en `.claude/commands/`. Puedes ver su implementación:
- `.claude/commands/generate-prp.md` - Vea cómo investiga y crea PRP
- `.claude/commands/execute-prp.md` - Vea cómo implementa funciones de PRP

La variable `$ARGUMENTS` en estos comandos recibe lo que pase después del nombre del comando (e.g., `INICIO.md` o `PRPs/nombre-de-tu-archivo.md`).

Este comando:
1. Lee tu solicitud de función
2. Investigar la base del código en busca de patrones
3. Búsqueda de documentación relevante
4. Crear un PRP integral en `PRPs/nombre-de-tu-archivo.md`

### 4. Executar el PRP

Una vez generado, ejecute el PRP para implementar su función:

```bash
/execute-prp PRPs/nombre-de-tu-archivo.md
```

La asistente de codificación AI:
1. Lea todo el contexto del PRP
2. Crear un plan de implementación detallado
3. Ejecutar cada paso con validación
4. Ejecute pruebas y solucione cualquier problema
5. Asegúrese de que se cumplan todos los criterios de éxito

## Escriba un arhivo INICIO.md efectivo

### Seciones clave Explicadas

**FEATURE**: Ser específica y completa
- ❌ "Construir un web scraper"
- ✅ "Cree un web scraper asincrónico con BeautifulSoup que extrae datos de productos de sitios de comercio electrónico, maneja la limitación de velocidad y almacena los resultados en PostgreSQL."

**EJEMPLOS**: Aprovechar el archivo examples/ folder
- Coloque patrones de código relevantes en `examples/`
- Referencia de archivos y patrones específicos a seguir
- Explicar qué aspectos deben imitar

**DOCUMENTACION**: Incluya todos los recursos relevantes
- Documentación API, URLs
- Guías de Librerías
- Documentación de servidores MCP
- Esquemas de Bases de Datos

**OTRAR CONSIDERACIONS**: Captura detalles importantes
- Requisitos de autenticación
- Límites de tarifas o cuotas
- Errores comunes
- Requisitos de rendimiento

## El flujo de trabajo del PRP

### Como trabaja /generate-prp 

El comando sigue el siguiente proceso:

1. **Fase de Investigación**
   - Analiza su base de código en busca de patrones
   - Búsquedas de implementaciones similares
   - Identifica las convenciones a seguir

2. **Recopilación de documentación**
   - Obtiene documentos API relevantes
   - Incluye documentación de la biblioteca.
   - Añade errores y peculiaridades.

3. **Creación de planes**
   - Crea un plan de implementación paso a paso.
   - Incluye controles de validación.
   - Añade requisitos de prueba.

4. **Control de calidad**
   - Califica el nivel de confianza (del 1 al 10)
   - Garantiza que se incluya todo el contexto

### Como trabaja el /execute-prp 

1. **Carga el Contexto**: Lee el PRP completamente
2. **Plan**: Crea una lista detallada de tareas usando TodoWrite
3. **Ejecuta**: Implementa cada componente
4. **Valida**: Corre tests y linting
5. **Itera**: Corrige cualquier problema encontrado
6. **Completa**: Garantiza que se cumplan todos los requisitos

Ver `PRPs/EXAMPLE_multi_agent_prp.md` para un ejemplo completo de lo que se genera.

## Usando Ejemplos de manera Efectiva

La carpeta`examplos/`  es **critica** para el éxito. Los asistentes de codificación de IA funcionan mucho mejor cuando pueden ver patrones a seguir.

### Qué incluir en los ejemplos

1. **Patrones de estructura de código**
   - Cómo organizar los módulos
   - Convenciones de importación
   - Patrones de clase/función

2. **Patrones de prueba**
   - Estructura del archivo de prueba
   - Enfoques de simulación
   - Estilos de aserción

3. **Patrones de integración**
   - Implementaciones de API de cliente
   - Conexiones a bases de datos
   - Flujos de autenticación

4. **Patrones CLI**
   - Análisis de argumentos
   - Formato de salida
   - Gestión de errores

### Estructura Ejemplo

```
ejemplos/
├── README.md         # Explica lo que demuestra cada ejemplo.
├── cli.py            # Patrón de implementación de CLI
├── agent/            # Patrones de arquitectura de agentes
│   ├── agent.py      # Patrón de creación de agentes
│   ├── tools.py      # Patrón de implementación de herramientas
│   └── providers.py  # Patrón multiproveedor
└── tests/            # Patrones de prueba
    ├── test_agent.py # Patrones de pruebas unitarias
    └── conftest.py   # Configuración de Pytest
```Asegúrese de que se cumplan todos los criterios de éxito

## Mejores Practicas

### 1. Sea explícito en INICIO.md
- No asuma que la IA conoce sus preferencias.
- Incluya requisitos y restricciones específicos.
- Haga referencia a ejemplos con liberalidad.

### 2. Proporcionar ejemplos completos
- Más ejemplos = mejores implementaciones
- Mostrar qué hacer y qué no hacer
- Incluir patrones de gestión de errores

### 3. Utilice puertas de validación
- Los PRP incluyen comandos de prueba que deben aprobarse.
- La IA iterará hasta que todas las validaciones sean exitosas.
- Esto garantiza que el código funcione a la primera.

### 4. Documentación de apalancamiento
- Incluir documentación oficial de la API
- Añadir recursos del servidor MCP
- Consultar secciones específicas de la documentación

### 5. Personalizar CLAUDE.md
- Añade tus convenciones
- Incluye reglas específicas del proyecto
- Define estándares de codificación

## Recursos

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Context Engineering Best Practices](https://www.philschmid.de/context-engineering)
