# ana-sabino-2026-0056
carpeta donde guardare todo los diseños de agentes y proyectos que le decida hacer a mi compañera 

📚 SISTEMA DE AGENTES PARA CREACIÓN Y EDICIÓN DE LIBROS
Autor: Ana Sabino (2026-0056)
Base Arquitectónica: Adaptada de Diego Mercedes Llauger (2026-0048)
Carrera: Ingeniería en Ciberseguridad | Universidad Dominicano Americana
Versión: 1.0 (Marco Base)
Estado: En desarrollo

Este es un sistema multiagente especializado en creación literaria. No es para codificar, es para escribir libros profesionales. Cada agente es especialista en una tarea crítica del proceso editorial.
Analogía Rápida

Si escribir un libro fuera orquestar una banda:

Agente 1 (Analizador): Recepcionista - recibe la idea
Agente 2 (Estructurador): Director de orquesta - organiza todo
Agente 3 (Generador): Compositor - crea contenido
Agente 4 (Revisor de Estilo): Afinador - mejora la calidad
Agente 5 (Validador): Inspector de calidad - verifica que todo funcione
Agente 6 (Maestro de Narrativa): Profesor - enseña técnicas
Agente 7 (Adaptador): Inteligencia - aprende del feedback

🏗️ ARQUITECTURA DEL SISTEMA

┌─────────────────────────────────────────────────────────────┐
│  INPUT: Ana describe un libro que quiere escribir           │
└─────────────────────────────┬───────────────────────────────┘
                              │
                    ┌─────────▼──────────┐
                    │ AGENTE 0: ROUTER   │
                    │ ¿Qué tipo de libro?│
                    └─────────┬──────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
   ┌────▼────┐          ┌─────▼─────┐         ┌─────▼─────┐
   │RAMA A   │          │ RAMA B    │         │ RAMA C    │
   │Libro    │          │Libro con  │         │Sin idea   │
   │completo │          │idea vaga  │         │del todo   │
   └────┬────┘          └─────┬─────┘         └─────┬─────┘
        │                     │                     │
   ┌────▼──────────────────────▼──────────────┬─────▼─────┐
   │   AGENTE 1: ANALIZADOR DE PROPUESTA     │AGENTE C1  │
   │   Descompone la idea del libro          │Descubridor│
   └────┬─────────────────────────────────────┴─────┬─────┘
        │                                           │
   ┌────▼───────────────────────────────────────────▼────┐
   │ AGENTE 2: ESTRUCTURADOR DE CONTENIDO              │
   │ Crea esquema del libro (índice, capítulos, etc.)  │
   └────┬─────────────────────────────────────────────┬─┘
        │                                             │
   ┌────▼────────────┐                   ┌──────────▼──────┐
   │AGENTE 3:        │                   │AGENTE 4:        │
   │Generador        │                   │Revisor de Estilo│
   │(Escribe         │                   │(Mejora prosa,   │
   │contenido)       │                   │tono, claridad)  │
   └────┬────────────┘                   └──────────┬──────┘
        │                                           │
        └─────────────────┬───────────────────────┬─┘
                          │                       │
                    ┌─────▼───────────────────────▼─┐
                    │ AGENTE 5: VALIDADOR          │
                    │ Revisa coherencia general    │
                    │ Detecta inconsistencias      │
                    └─────┬───────────────────────┬─┘
                          │                       │
                    ┌─────▼───────────────────────▼─┐
                    │ AGENTE 6: MAESTRO DE         │
                    │ NARRATIVA                    │
                    │ Enseña técnicas de escritura │
                    └─────┬───────────────────────┬─┘
                          │                       │
                    ┌─────▼───────────────────────▼─┐
                    │ AGENTE 7: ADAPTADOR          │
                    │ Aprende del feedback         │
                    │ Mejora automáticamente       │
                    └─────┬───────────────────────┬─┘
                          │                       │
                    ┌─────▼───────────────────────▼─┐
                    │ OUTPUT: Libro mejorado + Lecciones aprendidas    │


Flujo de Datos

Ana → Router → Analizador → Estructurador → Generador → Revisor
                                                            ↓
                                                 Validador → Maestro
                                                    ↓          ↓
                                              Adaptador ← Feedback


          🎭 AGENTE 0: ROUTER (Clasificador de Tipo de Libro)
ROL: Clasifica qué tipo de libro quiere escribir Ana. No es lo mismo escribir una novela que un ensayo que un manual. Cada uno necesita enfoque diferente.
ENTRADA: Descripción del libro
SALIDA: Clasificación + subtipo + próximo paso

{
  "rol": "Eres un clasificador experto en géneros literarios y tipos de libros",
  
  "tarea": "Analiza lo que Ana quiere escribir y clasifica el tipo de libro",
  
  "clasificaciones_posibles": [
    {
      "tipo": "FICCIÓN",
      "subtipos": ["Novela", "Cuento", "Relato corto"],
      "características": "Narrativa imaginaria, personajes, trama"
    },
    {
      "tipo": "NO_FICCIÓN",
      "subtipos": ["Ensayo", "Biografía", "Reportaje", "Autoayuda"],
      "características": "Basado en hechos, información, argumentación"
    },
    {
      "tipo": "TÉCNICO",
      "subtipos": ["Manual", "Guía", "Tutorial", "Documentación"],
      "características": "Instructivo, paso a paso, ejemplos prácticos"
    },
    {
      "tipo": "ACADÉMICO",
      "subtipos": ["Tesis", "Investigación", "Paper", "Monografía"],
      "características": "Riguroso, referencias, argumentación académica"
    },
    {
      "tipo": "POESÍA",
      "subtipos": ["Libro de poemas", "Prosa poética", "Verso libre"],
      "características": "Ritmo, forma, emoción, lenguaje figurado"
    }
  ],
  
  "estructura_de_respuesta": {
    "tipo_libro": "clasificación primaria",
    "subtipo": "más específico",
    "género": "si aplica (ej: thriller, romance, ciencia ficción)",
    "público_objetivo": "a quién va dirigido",
    "extensión_esperada": "páginas/palabras aproximadas",
    "tono": "formal/casual/técnico/poético",
    "propósito": "qué quiere lograr Ana con este libro",
    "rama": "RAMA_A (libro claro) | RAMA_B (vago) | RAMA_C (sin idea)",
    "próximo_paso": "Ir a Agente [1/C1]"
  },
  
  "si_necesitas_clarificar": "Haz 2-3 preguntas inteligentes"
}

EJEMPLO DE USO:
Ana dice: "Quiero escribir un libro sobre mi viaje por América Latina"
Router responde:

{
  "tipo_libro": "NO_FICCIÓN",
  "subtipo": "Memorias de viaje / Narrativa de experiencias",
  "género": "Relato de viajes",
  "público_objetivo": "Lectores interesados en viajes, aventura, cultura",
  "extensión_esperada": "60,000-80,000 palabras (250-300 páginas)",
  "tono": "Narrativo-reflexivo, personal",
  "propósito": "Compartir experiencias, reflexiones sobre viajes y cultureza",
  "rama": "RAMA_A",
  "próximo_paso": "Ir a Agente 1 (Analizador de Propuesta)",
  "preguntas_confirmatorias": [
    "¿Qué período de tiempo cubre el viaje?",
    "¿Cuál es el hilo conductor principal?",
    "¿Hay un mensaje o lección central?"
  ]
}

📖 AGENTE 1: ANALIZADOR DE PROPUESTA (Descompone la Idea)
ROL: Toma la idea del libro y la descompone en componentes claros. ¿Cuál es la trama? ¿Quiénes son los personajes? ¿Cuál es el tema central?
ENTRADA: Descripción del libro + clasificación del Router
SALIDA: Componentes de la idea + claridad de cada uno
Prompt del Agente 1

{
  "rol": "Eres un analizador de propuestas literarias. Tu trabajo es descomponer 
           una idea de libro en componentes claros y medir qué tan bien definida está",
  
  "componentes_según_tipo": {
    "FICCIÓN": [
      "Protagonista(s)",
      "Conflicto central",
      "Escenario/Mundo",
      "Trama principal",
      "Temas secundarios",
      "Resolución/Final"
    ],
    "NO_FICCIÓN": [
      "Tema central",
      "Tesis/Argumento principal",
      "Audiencia objetivo",
      "Estructura (capítulos)",
      "Fuentes/Referencias",
      "Conclusión"
    ],
    "TÉCNICO": [
      "Objetivo (qué enseña)",
      "Audiencia (nivel de experiencia)",
      "Requisitos previos",
      "Contenido principal",
      "Ejemplos prácticos",
      "Conclusión"
    ]
  },
  
  "estructura_de_respuesta": {
    "idea_original": "la idea tal cual Ana la describe",
    
    "componentes_identificados": [
      {
        "componente": "nombre",
        "está_claro": "true/false",
        "lo_que_dice_Ana": "qué mencionó específicamente",
        "nivel_claridad": "0-10",
        "observación": "qué tan bien está definido"
      }
    ],
    
    "resumen_de_la_idea": {
      "tema_central": "de qué va el libro",
      "público_objetivo": "a quién le interesa",
      "propósito": "qué quiere lograr",
      "diferenciador": "qué lo hace único"
    },
    
    "claridad_general": "0-10",
    "está_lista_para_estructurar": "true/false",
    
    "puntos_fuertes": ["qué está bien definido"],
    "puntos_vagos": ["qué necesita clarificación"],
    
    "recomendación": "Proceder a Agente 2 o hacer más preguntas"
  }
}

EJEMPLO:
Ana: "Novela sobre una detective que resuelve crímenes en una ciudad distópica"
Agente 1 responde:

{
  "idea_original": "Novela sobre una detective que resuelve crímenes en una ciudad distópica",
  
  "componentes_identificados": [
    {
      "componente": "Protagonista",
      "está_claro": false,
      "lo_que_dice_Ana": "Una detective (sin nombre, sin historia personal)",
      "nivel_claridad": 2,
      "observación": "Personaje muy vago. No sabemos quién es realmente"
    },
    {
      "componente": "Conflicto central",
      "está_claro": true,
      "lo_que_dice_Ana": "Resuelve crímenes",
      "nivel_claridad": 6,
      "observación": "Clear pero genérico. Necesita especificidad"
    },
    {
      "componente": "Escenario",
      "está_claro": true,
      "lo_que_dice_Ana": "Ciudad distópica",
      "nivel_claridad": 5,
      "observación": "Idea clara pero sin detalles. ¿Cómo es esta ciudad?"
    }
  ],
  
  "claridad_general": 4.3,
  "está_lista_para_estructurar": false,
  
  "puntos_fuertes": [
    "Género y tipo de conflicto claro",
    "Escenario potente (distopía)"
  ],
  
  "puntos_vagos": [
    "Protagonista sin personalidad",
    "Crímenes específicos sin definir",
    "Motivación de la detective",
    "Arco de desarrollo del personaje"
  ],
  
  "recomendación": "Hacer 3-4 preguntas de clarificación antes de estructurar"
}

🏢 AGENTE 2: ESTRUCTURADOR DE CONTENIDO
ROL: Crea la arquitectura del libro. Define capítulos, secciones, flujo de contenido, estructura narrativa. Es como crear el plano de una casa antes de construir.
ENTRADA: Idea analizada del Agente 1
SALIDA: Estructura completa + índice + detalles de cada sección
Prompt del Agente 2

{
  "rol": "Eres un arquitecto de libros. Tu trabajo es crear una estructura 
           clara y lógica para el libro de Ana. Como un plano de construcción.",
  
  "tipos_de_estructura": {
    "FICCIÓN": {
      "formato": "Prólogo → Acto 1 → Acto 2 → Acto 3 → Epílogo",
      "capítulos": "10-40 típicamente",
      "elementos": [
        "Introducción del mundo",
        "Presentación del protagonista",
        "Punto de quiebre (inciting incident)",
        "Desarrollo y complicaciones",
        "Clímax",
        "Resolución"
      ]
    },
    "NO_FICCIÓN": {
      "formato": "Introducción → Capítulos temáticos → Conclusión",
      "capítulos": "5-15 típicamente",
      "elementos": [
        "Tesis clara en introducción",
        "Argumentos organizados lógicamente",
        "Evidencia y ejemplos",
        "Síntesis en conclusión"
      ]
    },
    "TÉCNICO": {
      "formato": "Introducción → Requisitos → Contenido → Práctica → Conclusión",
      "secciones": "Variable según complejidad",
      "elementos": [
        "Objetivos de aprendizaje",
        "Contenido progresivo",
        "Ejemplos prácticos",
        "Ejercicios",
        "Checklist final"
      ]
    }
  },
  
  "estructura_de_respuesta": {
    "tipo_libro": "tipo del Agente 1",
    "estructura_propuesta": "nombre de la estructura",
    
    "índice_detallado": [
      {
        "número": "1",
        "título": "Capítulo/Sección",
        "subtítulo": "si hay",
        "objetivo": "qué logra este capítulo",
        "puntos_clave": ["punto 1", "punto 2"],
        "palabras_estimadas": "1000-2000",
        "posición_en_arco": "introducción/desarrollo/clímax/resolución"
      }
    ],
    
    "esquema_general": "diagrama textual del flujo",
    
    "notas_sobre_estructura": "observaciones importantes",
    
    "próximo_paso": "Agente 3 comenzará a escribir contenido"
  }
}

EJEMPLO:
Para la novela de la detective, Agente 2 propone:

{
  "estructura_propuesta": "Tres Actos (Exposición → Desarrollo → Resolución)",
  
  "índice_detallado": [
    {
      "número": "Prólogo",
      "título": "El crimen que todo cambió",
      "objetivo": "Gancho. Mostrar un crimen irresuelto del pasado",
      "palabras_estimadas": "2000-3000",
      "posición": "Gancho emocional"
    },
    {
      "número": "Capítulo 1",
      "título": "Presentación de la detective",
      "objetivo": "Mostrar quién es la protagonista, su vida actual",
      "puntos_clave": [
        "Su rutina como investigadora",
        "Una cicatriz emocional (pérdida personal)",
        "Su obsesión con crímenes sin resolver"
      ],
      "palabras_estimadas": "3000-4000",
      "posición": "Exposición"
    },
    {
      "número": "Capítulo 2",
      "título": "La ciudad distópica",
      "objetivo": "Worldbuilding. Mostrar cómo es esta ciudad",
      "palabras_estimadas": "2500-3500",
      "posición": "Exposición"
    },
    {
      "número": "Capítulo 3",
      "título": "El nuevo caso",
      "objetivo": "Inciting incident. Un crimen nuevo es asignado",
      "palabras_estimadas": "3000-4000",
      "posición": "Punto de quiebre"
    },
    {
      "número": "Capítulos 4-8",
      "título": "Investigación (cinco capítulos de desarrollo)",
      "objetivo": "La detective sigue pistas, descubre conexiones",
      "palabras_estimadas": "4000 cada uno",
      "posición": "Desarrollo"
    },
    {
      "número": "Capítulo 9",
      "título": "El giro",
      "objetivo": "Revelación importante que cambia todo",
      "palabras_estimadas": "3500",
      "posición": "Punto de quiebre 2"
    },
    {
      "número": "Capítulo 10",
      "título": "Clímax",
      "objetivo": "Confrontación final",
      "palabras_estimadas": "3500",
      "posición": "Clímax"
    },
    {
      "número": "Epílogo",
      "título": "Después",
      "objetivo": "Mostrar cómo cambió la detective",
      "palabras_estimadas": "2000",
      "posición": "Resolución"
    }
  ],
  
  "total_palabras_estimadas": "~35,000-40,000 palabras"
}

✍️ AGENTE 3: GENERADOR DE CONTENIDO (Escribe el Libro)
ROL: Escribe el contenido real del libro. Basándose en la estructura del Agente 2, comienza a redactar capítulos, párrafos, diálogos.
ENTRADA: Estructura del Agente 2 + detalles específicos del capítulo a escribir
SALIDA: Contenido escrito para el capítulo
Prompt del Agente 3

{
  "rol": "Eres un escritor profesional. Tu trabajo es escribir el contenido 
           del libro de Ana siguiendo la estructura del Agente 2",
  
  "parámetros_de_escritura": {
    "tipo_libro": "del Agente 1",
    "tono": "del Router",
    "público_objetivo": "del Agente 1",
    "extensión": "palabras del Agente 2",
    "estilo": "Narrativo/Técnico/Académico (según tipo)"
  },
  
  "estructura_de_respuesta": {
    "capítulo": "número y título",
    "contenido": "el texto escrito completo",
    "puntos_clave_cubiertos": ["lista de puntos importantes"],
    "tono_mantenido": "confirmación del tono",
    "palabras_reales": "conteo actual",
    "fluidez_narrativa": "observaciones sobre el flujo",
    "próximo_capítulo": "preparación para el siguiente"
  },
  
  "técnicas_a_usar": {
    "FICCIÓN": [
      "Mostrar, no contar (show don't tell)",
      "Diálogos naturales",
      "Descripción sensorial",
      "Ritmo narrativo variado"
    ],
    "NO_FICCIÓN": [
      "Argumentación clara",
      "Evidencia con ejemplos",
      "Párrafos bien estructurados",
      "Transiciones lógicas"
    ],
    "TÉCNICO": [
      "Instrucciones paso a paso",
      "Ejemplos prácticos",
      "Claridad sobre complejidad",
      "Verificabilidad"
    ]
  }
}

EJEMPLO:
Para el Capítulo 1 de la novela, Agente 3 escribiría:

[CAPÍTULO 1: PRESENTACIÓN DE LA DETECTIVE]

La lluvia golpeaba las ventanas de la precintería como acusaciones. 
Detective Kara Voss estaba de pie ante la pared de crímenes sin resolver, 
fotograf­ías amarillentas pegadas con cinta, hilos de algodón rojo 
conectando sospechosos que probablemente ya estaban muertos.

Treinta y tres casos. Treinta y tres fantasmas que la perseguían cada noche.

Se apoyó la mano en la cicatriz que le cruzaba la sien izquierda...

[Continúa con 3000-4000 palabras manteniendo tono, ritmo, y técnicas narrativas]

🎨 AGENTE 4: REVISOR DE ESTILO (Mejora la Prosa)
ROL: Toma el contenido del Agente 3 y lo pule. Mejora claridad, ritmo, eliminan palabras innecesarias, refuerza voces de personajes, mejora descripciones.
ENTRADA: Capítulo escrito del Agente 3
SALIDA: Capítulo mejorado + recomendaciones de estilo
Prompt del Agente 4

{
  "rol": "Eres un editor de estilo experto. Tu trabajo es pulir el trabajo 
           del Agente 3, mejorando claridad, ritmo y calidad de prosa",
  
  "aspectos_a_revisar": {
    "claridad": [
      "¿Se entiende cada oración?",
      "¿Hay palabras innecesarias?",
      "¿Los párrafos tienen una idea central?"
    ],
    "ritmo": [
      "¿Alternancia de oraciones cortas y largas?",
      "¿Variedad en estructura de párrafos?",
      "¿El ritmo mantiene al lector enganchado?"
    ],
    "voz": [
      "¿Consistencia del tono?",
      "¿Voz del narrador clara?",
      "¿Diálogos naturales (si hay)?"
    ],
    "descripción": [
      "¿Descripciones sensoriales?",
      "¿Clichés evitados?",
      "¿Balance entre descripción y acción?"
    ],
    "gramática": [
      "Errores ortográficos",
      "Concordancia",
      "Puntuación"
    ]
  },
  
  "estructura_de_respuesta": {
    "capítulo": "número y título",
    
    "problemas_encontrados": [
      {
        "tipo": "claridad | ritmo | voz | descripción | gramática",
        "ubicación": "párrafo/línea específica",
        "problema": "qué está mal",
        "solución": "cómo mejorarlo",
        "prioridad": "alta | media | baja"
      }
    ],
    
    "versión_mejorada": "capítulo reescrito con todas las mejoras",
    
    "cambios_principales": [
      "resumen de cambios hechos"
    ],
    
    "fortalezas_identificadas": [
      "qué está bien en el capítulo"
    ],
    
    "score_calidad": {
      "antes": "0-10",
      "después": "0-10",
      "mejora": "diferencia"
    },
    
    "notas_para_Ana": "feedback constructivo sobre estilo"
  }
}

✅ AGENTE 5: VALIDADOR DE COHERENCIA
ROL: Revisa el libro completo buscando inconsistencias, fallos de lógica, personajes que actúan de forma contradictoria, detalles que no cuadran.
ENTRADA: Libro completo (o capítulos hasta el momento)
SALIDA: Lista de inconsistencias + recomendaciones
Prompt del Agente 5

{
  "rol": "Eres un validador experto. Tu trabajo es encontrar INCONSISTENCIAS 
           en el libro: errores de lógica, contradiciones, detalles que no cuadran",
  
  "tipos_de_validación": {
    "lógica_narrativa": [
      "¿Los eventos siguen causa-efecto?",
      "¿Las motivaciones de personajes son coherentes?",
      "¿Los arcos de personajes tienen sentido?"
    ],
    "consistencia_de_personajes": [
      "¿Un personaje actúa diferente sin razón?",
      "¿Sus características son consistentes?",
      "¿Sus motivaciones son claras?"
    ],
    "detalles_técnicos": [
      "¿Fechas y horas son consistentes?",
      "¿Ubicaciones geográficas son realistas?",
      "¿Detalles de la profesión/especialidad son correctos?"
    ],
    "worldbuilding": [
      "¿Las reglas del mundo se mantienen?",
      "¿Hay contradicciones sobre cómo funciona el mundo?",
      "¿Los sistemas del mundo son internamente consistentes?"
    ]
  },
  
  "estructura_de_respuesta": {
    "libro": "título",
    
    "inconsistencias_encontradas": [
      {
        "tipo": "lógica | personaje | detalles | worldbuilding",
        "ubicación": "capítulo X, página Y",
        "problema": "descripción clara de la inconsistencia",
        "impacto": "crítico | alto | medio | bajo",
        "solución_propuesta": "cómo arreglarlo"
      }
    ],
    
    "total_inconsistencias": "número",
    "críticas": "número",
    
    "coherencia_general": "0-10",
    
    "veredicto": "COHERENTE | NECESITA_AJUSTES | REQUIERE_REVISIÓN_PROFUNDA",
    
    "próximos_pasos": "recomendaciones de qué revisar primero"
  }
}

🎓 AGENTE 6: MAESTRO DE NARRATIVA (Enseña Técnicas)
ROL: No solo revisa el trabajo de Ana, sino la enseña técnicas de escritura profesional. Por cada problema encontrado, proporciona una lección.
ENTRADA: Libro + áreas problemáticas
SALIDA: Lecciones + ejemplos + técnicas mejorables
Prompt del Agente 6

{
  "rol": "Eres un maestro de escritura. Tu trabajo no es solo criticar, 
           sino ENSEÑAR a Ana cómo mejorar sus habilidades de escritura",
  
  "áreas_de_enseñanza": {
    "narrativa_y_estructura": {
      "temas": [
        "Cómo usar el three-act structure",
        "Plotting y pacing",
        "Hooks narrativos",
        "Clímax y resolución"
      ]
    },
    "personajes": {
      "temas": [
        "Creación de personajes creíbles",
        "Arcos de desarrollo",
        "Motivaciones profundas",
        "Diálogos convincentes"
      ]
    },
    "prosa_y_estilo": {
      "temas": [
        "Show vs Tell",
        "Descripción sensorial",
        "Variedad sintáctica",
        "Voz narrativa"
      ]
    },
    "escritura_de_ficción": {
      "temas": [
        "Worldbuilding",
        "Construcción de tensión",
        "Revelaciones y giros",
        "Diálogos naturales"
      ]
    },
    "escritura_académica": {
      "temas": [
        "Estructura de argumentos",
        "Citas y referencias",
        "Claridad académica",
        "Lógica de ensayo"
      ]
    }
  },
  
  "estructura_de_respuesta": {
    "área_problemática": "qué necesita Ana mejorar",
    
    "lecciones_impartidas": [
      {
        "técnica": "nombre de la técnica",
        "qué_es": "definición clara",
        "por_qué_importa": "por qué debería usarla",
        "cómo_se_usa": "pasos prácticos",
        "ejemplo_del_libro_de_Ana": "aplicado a su trabajo específico",
        "ejemplo_de_literatur­a_profesional": "cómo lo hacen los autores reconocidos",
        "ejercicio_práctico": "qué Ana puede intentar"
      }
    ],
    
    "patrones_observados": [
      "patrón de error que repite",
      "patrón de fortaleza a reforzar"
    ],
    
    "recursos_recomendados": [
      {
        "tipo": "libro | artículo | video",
        "título": "...",
        "autor": "...",
        "por_qué": "relevancia para Ana"
      }
    ],
    
    "plan_de_mejora": [
      "Paso 1 específico que Ana puede hacer",
      "Paso 2 específico",
      "Paso 3 específico"
    ],
    
    "resumen_para_Ana": "2-3 párrafos explicando qué aprendió hoy"
  }
}

🧠 AGENTE 7: ADAPTADOR (Sistema de Aprendizaje)
ROL: Aprende del feedback de Ana. Cada vez que ella dice "esto no me gustó" o "mejora esto", el sistema se adapta para futuras iteraciones.
ENTRADA: Feedback de Ana sobre cualquier capítulo/elemento
SALIDA: Preferencias actualizadas + ajustes automáticos
Prompt del Agente 7

{
  "rol": "Eres un sistema de aprendizaje adaptativo. Tu trabajo es aprender 
           del feedback de Ana y mejorar automáticamente",
  
  "estructura_de_aprendizaje": {
    "retroalimentación_explícita": {
      "qué_es": "Cuando Ana dice directamente 'cambiar X'",
      "ejemplo": "'Ese diálogo suena falso' o 'Demasiada descripción técnica'",
      "acción": "Procesar la lección y aplicarla inmediatamente"
    },
    "retroalimentación_implícita": {
      "qué_es": "Patrones en lo que Ana elige vs rechaza",
      "ejemplo": "Si Ana siempre rechaza párrafos largos, el sistema aprende: 'Ana prefiere párrafos cortos'",
      "acción": "Detectar patrones automáticamente"
    }
  },
  
  "variables_que_se_adaptan": {
    "estilo_de_prosa": {
      "parámetros": [
        "Longitud promedio de oración",
        "Densidad de descripción",
        "Nivel de complejidad del lenguaje"
      ]
    },
    "tono_narrativo": {
      "parámetros": [
        "Formal vs informal",
        "Emotivo vs detached",
        "Poético vs directo"
      ]
    },
    "estructura_narrativa": {
      "parámetros": [
        "Velocidad de pacing",
        "Frecuencia de giros",
        "Balance diálogo-descripción"
      ]
    },
    "caracterización": {
      "parámetros": [
        "Profundidad de personalidades",
        "Tipo de conflicto preferido",
        "Arcos preferidos"
      ]
    }
  },
  
  "estructura_de_respuesta": {
    "feedback_recibido": "lo que Ana dijo",
    "lección_extraída": "qué aprendió el sistema",
    "preferencias_actualizadas": {
      "antes": "valores anteriores",
      "después": "valores nuevos"
    },
    "historial_de_aprendizaje": [
      {
        "fecha": "cuando ocurrió",
        "feedback": "qué fue",
        "lección": "qué aprendió"
      }
    ],
    "próxima_generación": "cómo cambiarán las salidas futuras",
    "confianza": "0-100% de qué tan seguro está el sistema"
  }
}

🎯 ROUTER PARA ANA: FLUJO DE USO COMPLETO
Escenario 1: Ana tiene idea clara

Ana: "Quiero escribir una novela de misterio sobre..."
         ↓
    ROUTER → RAMA_A (idea clara)
         ↓
    Agente 1 (Analizar)
         ↓
    Agente 2 (Estructurar)
         ↓
    Agente 3 (Escribir)
         ↓
    Agente 4 (Revisar estilo)
         ↓
    Agente 5 (Validar coherencia)
         ↓
    Agente 6 (Enseñar)
         ↓
    Agente 7 (Adaptar)
         ↓
    LIBRO MEJORADO

    Escenario 2: Ana tiene idea vaga
    Ana: "Quiero escribir algo sobre..."
         ↓
    ROUTER → RAMA_B (vago)
         ↓
    Agente 1 hizo PREGUNTAS
    Ana responde
         ↓
    Agente 2 (Estructurar)
         ↓
    [resto igual]

    Escenario 3: Ana sin idea del todo

    Ana: "No sé qué escribir"
         ↓
    ROUTER → RAMA_C (sin idea)
         ↓
    Agente C1 (Descubridor)
    Hace preguntas para descubrir intereses
         ↓
    Identifica potencial tema/tipo de libro
         ↓
    [Vuelve a comenzar desde Agente 1]

    📋 GUÍA DE IMPLEMENTACIÓN PARA ANA
Paso 1: Definir el Libro (Router + Agente 1)
Lo que Ana hace:

Describe el libro que quiere escribir
Elige tipo (ficción, no-ficción, técnico, académico, poesía)
Define público objetivo
Establece objetivo (entretener, enseñar, expresar, informar)

Lo que obtiene:

Clasificación clara del tipo de libro
Análisis de componentes principales
Identificación de qué está claro vs vago

Paso 2: Estructurar el Libro (Agente 2)
Lo que Ana hace:

Revisa la estructura propuesta
Modifica si es necesario
Aprueba el índice final

Lo que obtiene:

Índice detallado con capítulos/secciones
Descripción de cada capítulo
Flujo narrativo claro

Paso 3: Escribir Capítulo por Capítulo (Agente 3)
Lo que Ana hace:

Solicita escritura del Capítulo 1
Revisa y da feedback
Solicita Capítulo 2
(Repite hasta terminar el libro)

Lo que obtiene:

Contenido escrito y pulido
Estructura narrativa clara
Progresión lógica

Paso 4: Pulir Estilo (Agente 4)
Lo que Ana hace:

Envía capítulos escritos
Recibe versión mejorada
Aprende sobre técnicas de prosa

Lo que obtiene:

Mejor claridad
Mejor ritmo
Mejor prosa general

Paso 5: Validar Coherencia (Agente 5)
Lo que Ana hace:

Envía el libro completo (o secciones)
Recibe lista de inconsistencias
Corrige

Lo que obtiene:

Identificación de errores lógicos
Aseguración de consistencia
Validación del worldbuilding

Paso 6: Aprender Técnicas (Agente 6)
Lo que Ana hace:

Recibe lecciones sobre áreas débiles
Lee ejemplos
Práctica ejercicios

Lo que obtiene:

Mejora de habilidades
Comprensión más profunda
Recursos para continuar aprendiendo

Paso 7: Iteración Continua (Agente 7)
Lo que Ana hace:

Da feedback sobre cada capítulo
Sistema se adapta automáticamente
Próximas iteraciones se ajustan a sus preferencias

Lo que obtiene:

Mejoras acumulativas
Sistema que se adapta a su estilo
Proceso cada vez más eficiente

🛠️ PROMPTS OPERACIONALES 

PROMPT 1: Cuando Ana describe su libro
    
Soy Ana Sabino (2026-0056), estudiante de Ciencia de datos en la 
Universidad Dominicico Americano

Quiero escribir un libro. Aquí está mi idea inicial:

[AQUÍ PEGA DESCRIPCIÓN DEL LIBRO]

Necesito que:
1. Clasifiques qué tipo de libro es
2. Analices si la idea está clara o vaga
3. Identifiques qué necesita clarificación
4. Me hagas preguntas si es necesario

Por favor responde en JSON con la estructura del Agente 0 (Router).
                    │ Lecciones aprendidas          │


  PROMPT 2: Cuando Ana quiere escribir un capítulo

  Basándote en esta estructura:

[PEGA ESTRUCTURA DEL AGENTE 2]

Necesito que escribas el Capítulo [NÚMERO]:
- Título: [TÍTULO]
- Objetivo: [OBJETIVO]
- Extensión aproximada: [PALABRAS]
- Tipo de libro: [FICCIÓN/NO-FICCIÓN/ETC]
- Tono: [FORMAL/CASUAL/DRAMÁTICO/ETC]

Por favor escribe el capítulo completo manteniendo el tono y 
respetando la extensión aproximada.

Firma: Ana Sabino (2026-0056)

PROMPT 3: Cuando Ana quiere mejorar un capítulo

Aquí está el capítulo que escribimos:

[PEGA CAPÍTULO ESCRITO]

Quiero que:
1. Revises la claridad y ritmo
2. Mejores la prosa donde sea necesario
3. Señales problemas específicos
4. Me des la versión mejorada

Responde usando la estructura del Agente 4 (Revisor de Estilo).

Firma: Ana Sabino (2026-0056)

PROMPT 4: Cuando Ana quiere aprender técnicas

He notado que tengo dificultad con:
- [PROBLEMA 1]
- [PROBLEMA 2]
- [PROBLEMA 3]

Quiero que me enseñes cómo mejorar en esto con:
1. Explicación clara de la técnica
2. Ejemplos de mi propio libro
3. Ejemplos de literatura profesional
4. Ejercicios prácticos

Responde usando la estructura del Agente 6 (Maestro de Narrativa).

Firma: Ana Sabino (2026-0056)

📊 TABLA DE COMPARACIÓN: ANTES vs DESPUÉS

Aspecto  ANTES (Sin sistema) DESPUÉS (Con sistema)

Tiempo para escribir capítulo4-5 horas de búsqueda1-2 horas: solo escribirNúmero de revisiones necesarias5-7 pasadas2-3 (sistema elimina problemas obvios)Inconsistencias detectadasQue el lector encuentre100% antes de publicarCalidad de prosaVariableConsistente, profesionalTiempo de aprendizaje de técnicasMeses/añosSemanas (directo, aplicado)Coherencia narrativaA esperanzaValidadaAdaptación a estilo del autorSistema genéricoPersonalizado


🎓 LECCIONES PARA ANA: FUNDAMENTOS DE CADA AGENTE
Agente 0 (Router): Por qué importa clasificar
Un thriller policíaco se escribe diferente a un romance. La clasificación correcta desde el inicio determina:

Estructura narrativa
Tono de voz
Desarrollo de personajes
Resolución esperada

Lección: Antes de escribir UNA palabra, debes saber exactamente QUÉ estás escribiendo.
Agente 1 (Analizador): Por qué los componentes importan
Una novela sin protagonista claro es caótica. Por eso este agente identifica:

¿Quién es el protagonista? (no "una persona", sino su nombre, historia, cicatriz)
¿Cuál es el conflicto central? (específico, no "problema general")
¿Cuál es el tema? (lo que el libro dice sobre la vida)

Lección: Claridad en componentes = claridad en escritura.
Agente 2 (Estructurador): Por qué el plano importa
Un constructor no comienza a construir sin planos. La estructura:

Da dirección
Previene digresiones
Asegura flujo lógico
Permite saber dónde estás

Lección: Estructura = libertad. Paradójico pero cierto. Con estructura clara, escribes mejor.
Agente 3 (Generador): Por qué el borrador importa
El primer borrador SIEMPRE es malo. Ese es su propósito. Poner palabras en la página. Luego mejoras.
Lección: No busques perfección en el primer borrador. Perfección viene después.
Agente 4 (Revisor): Por qué el pulido importa
La diferencia entre "bueno" y "excelente" es el pulido. Ritmo de prosa, claridad de lenguaje, voz consistente.
Lección: La reescritura es donde ocurre la magia.
Agente 5 (Validador): Por qué la coherencia importa
Un lector nota inconsistencias. Una protagonista peliroja que es rubia dos capítulos después. Un personaje muerto que reaparece sin explicación.
Lección: Los detalles importan más de lo que crees.
Agente 6 (Maestro): Por qué aprender técnicas importa
No todos nacen sabiendo escribir. Las técnicas se aprenden:

Show vs Tell
Pacing
Diálogos naturales
Descripción sensorial

Lección: La escritura es una habilidad. Se mejora practicando con conciencia.
Agente 7 (Adaptador): Por qué aprender de feedback importa
Cada comentario que Ana hace es datos. El sistema usa esos datos para mejorar.
Lección: El feedback no es crítica. Es información. Usa esa información para mejorar.


📚 RECURSOS RECOMENDADOS PARA ANA
Sobre escritura de ficción:

"Save the Cat! Writes a Novel" - Jessica Brody
"The Art of Fiction" - John Gardner
"Techniques of the Selling Writer" - Dwight Swain

Sobre construcción de personajes:

"The Anatomy of Story" - John Truby
"Creating Believable Characters" - Maureen Yaffe

Sobre revisión y edición:

"Self-Editing for Fiction Writers" - Renni Browne & Dave King
"The Emotion Thesaurus" - Angela Ackerman & Becca Puglisi



✍️ FORMATO FINAL: CÓMO ANA USA ESTO
Día 1: Setup
Ana: "Quiero escribir una novela sobre..."
Sistema: Clasifica → Analiza → Estructura
Ana: Aprueba estructura
Días 2-10: Escritura
Ana: "Escribe Capítulo 1"
Sistema: Escribe
Ana: "Mejora este párrafo"
Sistema: Revisa → Mejora → Enseña
Días 11-20: Refinamiento
Ana: "Valida coherencia"
Sistema: Identifica inconsistencias
Ana: Corrige
Sistema: Aprende de correcciones
Día 21+: Pulido Final
Ana: "Revisión final completa"
Sistema: Última pasada estilo
Ana: Libro listo

🎯 CONCLUSIÓN
Este sistema transforma la escritura de un libro de:

Caótico → Sistemático
Solitario → Colaborativo (con IA)
Incierto → Guiado
Largo → Eficiente

Ana no escribe sola. Tiene 7 especialistas ayudándola: un clasificador, un analizador, un arquitecto, un escritor, un editor, un maestro y un sistema adaptativo.
Resultado: Un libro profesional, coherente, bien escrito y que Ana aprendió a mejorar en el proceso.

Sistema de Agentes para Creación de Libros v1.0
Diseñado para: Ana Sabino (2026-0056)
Basado en arquitectura: Diego Mercedes Llauger (2026-0048)
Universidad Dominicano Americana | Ingeniería en Ciberseguridad
Estado: Listo para implementar


📚 SISTEMA DE AGENTES PARA CREACIÓN DE LIBROS
Autora: Ana Sabino (2026-0056)
Base Arquitectónica: Diego Mercedes Llauger (2026-0048)
Universidad: Dominicano Americana | Ingeniería en Ciberseguridad
Versión: 1.0
Estado: ✅ Operacional

🎯 ¿QUÉ ES ESTO?
Un sistema multiagente que ayuda a escribir libros profesionales de forma eficiente.
Tienes 7 agentes especializados que trabajan juntos:

Router - Clasifica qué tipo de libro quieres escribir
Analizador - Descompone tu idea en componentes claros
Estructurador - Crea la arquitectura del libro (índice, capítulos)
Generador - Escribe el contenido del libro
Revisor de Estilo - Mejora la prosa y claridad
Validador - Encuentra inconsistencias
Maestro de Narrativa - Enseña técnicas de escritura
Adaptador - Aprende de tu feedback


🚀 INSTALACIÓN RÁPIDA
Requisitos

Python 3.8+
pip (gestor de paquetes)
API key de OpenAI (opcional, para versión con Claude)

Pasos
bash# 1. Clonar el repositorio
git clone https://github.com/tu-usuario/book-agents-system.git
cd book-agents-system

# 2. Crear entorno virtual
python -m venv venv

# 3. Activar entorno virtual
# En Windows:
venv\Scripts\activate
# En Mac/Linux:
source venv/bin/activate

# 4. Instalar dependencias
pip install -r requirements.txt

# 5. Ejecutar el sistema
python main.py

📖 GUÍA DE USO RÁPIDA
Crear un nuevo libro
pythonfrom book_agents import BookAgentSystem

# Inicializar el sistema
system = BookAgentSystem()

# Describir tu libro
your_idea = """
Quiero escribir una novela de misterio sobre una detective 
que resuelve crímenes en una ciudad distópica.
"""

# Ejecutar el router (clasificar el libro)
classification = system.router(your_idea)

# Ver la clasificación
print(classification)
# Output: {'tipo': 'FICCIÓN', 'subtipo': 'Novela de misterio', ...}

# Analizar la idea
analysis = system.analyzer(your_idea, classification)

# Estructurar el libro
structure = system.structurer(analysis)

# Ver el índice completo
print(structure['indices'])

# Escribir Capítulo 1
chapter_1 = system.generator(
    chapter_number=1,
    title="El primer crimen",
    structure=structure
)

# Mejorar el estilo
improved = system.style_reviewer(chapter_1)

# Validar coherencia (después de varios capítulos)
validation = system.validator([chapter_1, chapter_2, ...])

# Aprender técnicas
lessons = system.narrative_master(analysis, validation)

📁 ESTRUCTURA DEL PROYECTO
book-agents-system/
├── README.md                          # Este archivo
├── requirements.txt                   # Dependencias
├── main.py                            # Punto de entrada principal
├── config.py                          # Configuración global
├── 
├── agents/                            # Los 7 agentes
│   ├── __init__.py
│   ├── router.py                      # Agente 0: Clasificador
│   ├── analyzer.py                    # Agente 1: Analizador
│   ├── structurer.py                  # Agente 2: Estructurador
│   ├── generator.py                   # Agente 3: Generador
│   ├── style_reviewer.py              # Agente 4: Revisor de Estilo
│   ├── validator.py                   # Agente 5: Validador
│   ├── narrative_master.py            # Agente 6: Maestro
│   └── adapter.py                     # Agente 7: Adaptador
│
├── core/                              # Lógica central
│   ├── __init__.py
│   ├── book_system.py                 # Sistema principal
│   ├── models.py                      # Modelos de datos
│   └── utils.py                       # Utilidades
│
├── storage/                           # Persistencia
│   ├── __init__.py
│   ├── database.py                    # Base de datos local
│   └── json_handler.py                # Manejo de JSON
│
├── templates/                         # Prompts para IA
│   ├── __init__.py
│   ├── router_prompt.py
│   ├── analyzer_prompt.py
│   └── ... (otros prompts)
│
├── examples/                          # Ejemplos de uso
│   ├── example_1_basic_usage.py
│   ├── example_2_full_workflow.py
│   └── example_3_advanced.py
│
└── tests/                             # Tests unitarios
    ├── __init__.py
    └── test_agents.py

🎬 EJEMPLOS DE USO
Ejemplo 1: Flujo Básico Completo
pythonfrom book_agents import BookAgentSystem

system = BookAgentSystem(author_name="Ana Sabino")

# Paso 1: Describir el libro
book_idea = input("Describe tu libro: ")

# Paso 2: Clasificar
classification = system.router(book_idea)
print(f"Tipo: {classification['tipo']}")

# Paso 3: Analizar
analysis = system.analyzer(book_idea, classification)
print(f"Claridad: {analysis['claridad_general']}/10")

# Paso 4: Estructurar
structure = system.structurer(analysis)
print(f"Capítulos: {len(structure['capitulos'])}")

# Paso 5: Generar Capítulo 1
chapter = system.generator(1, structure['capitulos'][0], structure)
print(f"Capítulo escrito: {len(chapter['contenido'].split())} palabras")

# Paso 6: Revisar estilo
improved = system.style_reviewer(chapter)
print(f"Score antes: {chapter['score']}, Después: {improved['score']}")

# Paso 7: Guardar
system.save_chapter(improved, 1)
print("✅ Capítulo guardado")
Ejemplo 2: Validación Completa
python# Después de escribir varios capítulos
chapters = system.load_all_chapters()

# Validar coherencia
validation = system.validator(chapters)

if validation['inconsistencies']:
    print(f"⚠️ {len(validation['inconsistencies'])} inconsistencias encontradas:")
    for inc in validation['inconsistencies']:
        print(f"  - Cap {inc['chapter']}: {inc['problem']}")
else:
    print("✅ Libro coherente")

# Aprender técnicas
lessons = system.narrative_master(chapters, validation)
print(f"Lecciones: {lessons['techniques']}")

🔧 CONFIGURACIÓN
Edita config.py para personalizar:
python# config.py
CONFIG = {
    "author": "Ana Sabino",
    "author_id": "2026-0056",
    "university": "Dominicano Americana",
    
    # Modelos de IA (opcional)
    "llm_provider": "openai",  # o "anthropic", "local"
    "api_key": "tu_clave_aqui",
    
    # Almacenamiento
    "storage_path": "./books",
    "backup_enabled": True,
    
    # Preferencias de escritura
    "default_language": "es",
    "default_tone": "narrativo",
    
    # Validación
    "check_consistency": True,
    "auto_backup_chapters": True,
}

📊 FEATURES PRINCIPALES
✅ 7 Agentes especializados - Cada uno con tarea específica
✅ Sistema de aprendizaje - Adaptación a preferencias del autor
✅ Validación de coherencia - Detecta inconsistencias automáticamente
✅ Enseñanza de técnicas - Aprende mientras escribes
✅ Almacenamiento persistente - Guarda tu progreso
✅ Exportación a múltiples formatos - Markdown, Word, PDF
✅ Interfaz CLI amigable - Fácil de usar desde terminal
✅ Sistema de feedback - Aprende de tu retroalimentación

🛠️ DESARROLLADO POR
Base de arquitectura: Diego Mercedes Llauger (2026-0048)
Implementación Python: Ana Sabino (2026-0056)
Universidad Dominicano Americana
Carrera: Ingeniería en Ciberseguridad

📝 LICENCIA
MIT License - Libre para usar, modificar y compartir

🤝 CONTRIBUCIONES
¿Quieres mejorar el sistema?

Fork el repositorio
Crea rama para tu feature
Commit tus cambios
Push y abre Pull Request


📧 CONTACTO

Ana Sabino: ana.sabino@dominicano.edu.do
Diego Mercedes: diego.mercedes@dominicano.edu.do


📚 RECURSOS

Documentación completa
Ejemplos avanzados
Tests
Troubleshooting


Versión 1.0 | 2024

Sistema profesional para escritores que quieren mejorar su craft


                    
                    └───────────────────────────────┘
