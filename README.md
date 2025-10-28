# Plantilla Context Engineering

Una plantilla completa para comenzar con Context Engineering: la disciplina de Context Engineering para asistentes de codificación de IA para que tengan la información necesaria para realizar el trabajo de principio a fin.
> **Context Engineering is 10x mejor que prompt engineering y 100x mejor vibe coding.**

## 🚀 Quick Start

```bash
# 1. Clone esta plantilla
git clone https://github.com/elipirela/Context-Engineering-espanol.git
cd Context-Engineering-espanol

# 2. Configura las reglas del projecto (opcional - plantilla proporcionada)
# Edita CLAUDE.md para agregar las guías específicas de tu proyecto

# 3. Agrega ejemplos (muy recomendado)
# Coloca ejemplos relevantes de codigo en la carpeta de ejemplos

# 4. Crea tu requerimiento de funcioes iniciales
# Edita INICIO.md utilizando tus requerimientos de funiciones 

# 5. Generar un PRP funcional (Product Requirements Prompt)
# En Claude Code, run:
/generate-prp INICIO.md

# 6. Executar el PRP para implementar tus funciones
# En Claude Code, run:
/execute-prp PRPs/your-feature-name.md
```

## 📚 Table of Contents

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

1. **Reduce las fallas de AI**: MLas fallas del agente ost no son fallas del modelo, son fallas del contexto.
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
│   │   └── prp_base.md       # Plantilla base para PRP
│   └── EXAMPLE_multi_agent_prp.md  # Ejemplo de un PRP completo
├── ejemplos/                  # Ejemplos de codigo (critical!)
├── CLAUDE.md                 # Reglas globales para el asistente de IA
├── INICIO.md               # Plantilla para solicitudes de funciones
├── INITIAL_EXAMPLE.md       # Ejemplo de solicitud de función
└── README.md                # Este archivo
```


## Guía paso a paso

### 1. Configura reglas globales (CLAUDE.md)

El archivo `CLAUDE.md` contiene las reglas generales del proyecto que el asistente de IA seguirá en cada conversación. La plantilla incluye:

- **Reconocimiento del Projecto**: Lectura de documentos de planificación, comprobación de tareas
- **Estructura de Codigo**: Límites de tamaño de archivo, organización del módulo
- **Requerimientos de pruebas**: Patrones de pruebas unitarias, expectativas de cobertura
- **Convenciones de estilos**: Preferencias de idioma, reglas de formato
- **Estándares de la Documentación**: Formatos de cadenas de documentación, prácticas de comentarios

**Puede utilizar la plantilla proporcionada tal como está o personalizarla para su proyecto..**

### 2. Crea tu requierimiento inicial de funciones

Edit `INITIAL.md` to describe what you want to build:

```markdown
## FEATURE:
[Describe what you want to build - be specific about functionality and requirements]

## EXAMPLES:
[List any example files in the examples/ folder and explain how they should be used]

## DOCUMENTATION:
[Include links to relevant documentation, APIs, or MCP server resources]

## OTHER CONSIDERATIONS:
[Mention any gotchas, specific requirements, or things AI assistants commonly miss]
```

**See `INITIAL_EXAMPLE.md` for a complete example.**

### 3. Generate the PRP

PRPs (Product Requirements Prompts) are comprehensive implementation blueprints that include:

- Complete context and documentation
- Implementation steps with validation
- Error handling patterns
- Test requirements

They are similar to PRDs (Product Requirements Documents) but are crafted more specifically to instruct an AI coding assistant.

Run in Claude Code:
```bash
/generate-prp INITIAL.md
```

**Note:** The slash commands are custom commands defined in `.claude/commands/`. You can view their implementation:
- `.claude/commands/generate-prp.md` - See how it researches and creates PRPs
- `.claude/commands/execute-prp.md` - See how it implements features from PRPs

The `$ARGUMENTS` variable in these commands receives whatever you pass after the command name (e.g., `INITIAL.md` or `PRPs/your-feature.md`).

This command will:
1. Read your feature request
2. Research the codebase for patterns
3. Search for relevant documentation
4. Create a comprehensive PRP in `PRPs/your-feature-name.md`

### 4. Execute the PRP

Once generated, execute the PRP to implement your feature:

```bash
/execute-prp PRPs/your-feature-name.md
```

The AI coding assistant will:
1. Read all context from the PRP
2. Create a detailed implementation plan
3. Execute each step with validation
4. Run tests and fix any issues
5. Ensure all success criteria are met

## Writing Effective INITIAL.md Files

### Key Sections Explained

**FEATURE**: Be specific and comprehensive
- ❌ "Build a web scraper"
- ✅ "Build an async web scraper using BeautifulSoup that extracts product data from e-commerce sites, handles rate limiting, and stores results in PostgreSQL"

**EXAMPLES**: Leverage the examples/ folder
- Place relevant code patterns in `examples/`
- Reference specific files and patterns to follow
- Explain what aspects should be mimicked

**DOCUMENTATION**: Include all relevant resources
- API documentation URLs
- Library guides
- MCP server documentation
- Database schemas

**OTHER CONSIDERATIONS**: Capture important details
- Authentication requirements
- Rate limits or quotas
- Common pitfalls
- Performance requirements

## The PRP Workflow

### How /generate-prp Works

The command follows this process:

1. **Research Phase**
   - Analyzes your codebase for patterns
   - Searches for similar implementations
   - Identifies conventions to follow

2. **Documentation Gathering**
   - Fetches relevant API docs
   - Includes library documentation
   - Adds gotchas and quirks

3. **Blueprint Creation**
   - Creates step-by-step implementation plan
   - Includes validation gates
   - Adds test requirements

4. **Quality Check**
   - Scores confidence level (1-10)
   - Ensures all context is included

### How /execute-prp Works

1. **Load Context**: Reads the entire PRP
2. **Plan**: Creates detailed task list using TodoWrite
3. **Execute**: Implements each component
4. **Validate**: Runs tests and linting
5. **Iterate**: Fixes any issues found
6. **Complete**: Ensures all requirements met

See `PRPs/EXAMPLE_multi_agent_prp.md` for a complete example of what gets generated.

## Using Examples Effectively

The `examples/` folder is **critical** for success. AI coding assistants perform much better when they can see patterns to follow.

### What to Include in Examples

1. **Code Structure Patterns**
   - How you organize modules
   - Import conventions
   - Class/function patterns

2. **Testing Patterns**
   - Test file structure
   - Mocking approaches
   - Assertion styles

3. **Integration Patterns**
   - API client implementations
   - Database connections
   - Authentication flows

4. **CLI Patterns**
   - Argument parsing
   - Output formatting
   - Error handling

### Example Structure

```
examples/
├── README.md           # Explains what each example demonstrates
├── cli.py             # CLI implementation pattern
├── agent/             # Agent architecture patterns
│   ├── agent.py      # Agent creation pattern
│   ├── tools.py      # Tool implementation pattern
│   └── providers.py  # Multi-provider pattern
└── tests/            # Testing patterns
    ├── test_agent.py # Unit test patterns
    └── conftest.py   # Pytest configuration
```

## Best Practices

### 1. Be Explicit in INITIAL.md
- Don't assume the AI knows your preferences
- Include specific requirements and constraints
- Reference examples liberally

### 2. Provide Comprehensive Examples
- More examples = better implementations
- Show both what to do AND what not to do
- Include error handling patterns

### 3. Use Validation Gates
- PRPs include test commands that must pass
- AI will iterate until all validations succeed
- This ensures working code on first try

### 4. Leverage Documentation
- Include official API docs
- Add MCP server resources
- Reference specific documentation sections

### 5. Customize CLAUDE.md
- Add your conventions
- Include project-specific rules
- Define coding standards

## Resources

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Context Engineering Best Practices](https://www.philschmid.de/context-engineering)
