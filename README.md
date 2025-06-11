Un sistema inteligente para generar y realizar exámenes personalizados desde documentos de Google Docs, con opciones de respuesta generadas automáticamente por IA.
✨ Características

📖 Extracción automática de preguntas desde Google Docs
🤖 Generación automática de opciones usando IA (OpenAI/compatible)
🎯 Exámenes interactivos en terminal con navegación por teclado
📊 Sistema de puntuación con penalización por errores
💾 Guardado automático de exámenes y resultados
⚙️ Configuración flexible para diferentes materias
📈 Estadísticas detalladas al finalizar el examen

🚀 Instalación
Prerrequisitos

Node.js 14+ instalado
Cuenta de Google Cloud Platform
API key de OpenAI (o API compatible)

Paso 1: Clonar el repositorio
bashgit clone https://github.com/tu-usuario/sistema-examen-personalizado.git
cd sistema-examen-personalizado
Paso 2: Instalar dependencias
bashnpm install
Paso 3: Configurar Google Cloud

Ve a Google Cloud Console
Crea un nuevo proyecto o selecciona uno existente
Habilita la API de Google Docs
Crea credenciales de servicio:

Ve a "Credenciales" → "Crear credenciales" → "Cuenta de servicio"
Descarga el archivo JSON de credenciales
Renómbralo como credentials.json y colócalo en la raíz del proyecto



Paso 4: Configurar variables de entorno
Crea un archivo .env en la raíz del proyecto:
env# API de IA
AI_API_KEY=tu_api_key_aqui
AI_API_ENDPOINT=https://api.openai.com/v1/chat/completions
AI_MODEL=gpt-3.5-turbo

# Google Docs
GOOGLE_DOCUMENT_ID=tu_id_documento_google_docs

# Configuración de materia
SUBJECT_NAME=Biología Molecular
SUBJECT_EMOJI=🧬
SUBJECT_CONTEXT=biología molecular y genética
EXAM_DURATION=2 horas
EXAM_FORMAT=Tipo test (60%) + Preguntas escritas (40%)
PENALTY=1/4 punto por error
PASSING_GRADE=5.0
MAX_QUESTIONS=20

# Formato de preguntas (opcional)
QUESTION_FORMAT=default
Paso 5: Preparar el documento de Google Docs

Crea un documento en Google Docs con tus preguntas
Comparte el documento con la cuenta de servicio (email encontrado en credentials.json)
Copia el ID del documento desde la URL (la parte entre /d/ y /edit)

Formatos de preguntas soportados:

Default: Cualquier línea que contenga palabras clave como "qué", "cómo", "cuál", etc.
Asterisco: Preguntas que terminan con *
Numerado: Preguntas que empiezan con Q1., Q2., etc.

Ejemplo de documento:
¿Qué es la transcripción del ADN?
¿Cómo se realiza la replicación semiconservativa?
¿Cuál es la función de los ribosomas?
Explica el proceso de traducción de proteínas.
🎮 Uso
Ejecutar el programa
bashnpm start
Menú principal
El sistema te presentará 3 opciones:

📚 Generar nuevo examen: Crea un examen desde el documento de Google Docs
📂 Cargar examen existente: Reutiliza un examen previamente generado
❌ Salir: Cierra el programa

Controles durante el examen

A, B, C, D: Seleccionar respuesta
ESPACIO: Saltar pregunta
Q: Terminar examen anticipadamente

Resultados
Al finalizar el examen obtendrás:

⏱️ Tiempo total empleado
📊 Estadísticas de respuestas (correctas/incorrectas/saltadas)
🎯 Puntuación final con penalización
📈 Nota sobre 10
🎓 Resultado (aprobado/suspenso)

⚙️ Configuración Avanzada
Variables de entorno disponibles
VariableDescripciónValor por defectoSUBJECT_NAMENombre de la materia"MATERIA DE ESTUDIO"SUBJECT_EMOJIEmoji representativo"📚"SUBJECT_CONTEXTContexto para la IA"materia académica"EXAM_DURATIONDuración estimada"2 horas"EXAM_FORMATFormato del examen"Tipo test (60%) + Preguntas escritas (40%)"PENALTYPenalización por error"1/4 punto por error"PASSING_GRADENota mínima para aprobar5.0MAX_QUESTIONSMáximo de preguntas20QUESTION_FORMATFormato de preguntas"default"
Personalización de prompts
Para modificar cómo la IA genera las opciones, edita la función generarOpcionesParaPregunta() en el código.
📁 Estructura de archivos
sistema-examen-personalizado/
├── index.js                 # Código principal
├── package.json             # Dependencias
├── .env                     # Variables de entorno
├── credentials.json         # Credenciales de Google (no incluir en git)
├── examen_[timestamp].json  # Exámenes generados
├── resultados_[timestamp].json # Resultados de exámenes
└── README.md               # Este archivo
🔧 Dependencias

googleapis: Interacción con Google Docs API
dotenv: Manejo de variables de entorno
readline: Interfaz de terminal interactiva
fs: Sistema de archivos (nativo de Node.js)

🐛 Solución de problemas
Error: "AI_API_KEY no configurada"

Verifica que el archivo .env existe y contiene AI_API_KEY=tu_clave_aqui

Error: "GOOGLE_DOCUMENT_ID no configurado"

Asegúrate de que GOOGLE_DOCUMENT_ID esté en el archivo .env
Verifica que el ID del documento es correcto

Error: "credentials.json no encontrado"

Descarga las credenciales de Google Cloud Console
Coloca el archivo en la raíz del proyecto con el nombre exacto credentials.json

Error: "No se pudieron obtener preguntas del documento"

Verifica que el documento está compartido con la cuenta de servicio
Comprueba que el documento contiene preguntas en el formato correcto

Error de API de IA

Verifica que tu API key de OpenAI es válida
Comprueba que tienes créditos suficientes en tu cuenta
Revisa la configuración de AI_API_ENDPOINT y AI_MODEL

💡 Consejos de uso
Para mejores resultados:

Preguntas claras: Formula preguntas específicas y técnicas en tu documento
Contexto apropiado: Configura SUBJECT_CONTEXT con terminología específica de tu materia
Número de preguntas: Empieza con 5-10 preguntas para probar el sistema
Revisión manual: Verifica las opciones generadas antes de usar el examen

Formato recomendado para el documento:
¿Qué enzima cataliza la replicación del ADN?
¿Cuál es la función principal del retículo endoplasmático rugoso?
Explica el proceso de mitosis en células eucariotas.
¿Cómo se diferencia la transcripción de la traducción?
