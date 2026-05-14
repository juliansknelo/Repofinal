# GEMINI.md — Instrucciones para escritura en LaTeX (Reporte Final de Residencia Profesional)

> Este documento define las reglas, estructura y convenciones que **todo modelo de IA** debe seguir al generar contenido LaTeX para el Reporte Final de Residencia Profesional del **Tecnológico Nacional de México / Instituto Tecnológico de Veracruz**.

---

## 1. Clase de documento y geometría de página

```latex
\documentclass[12pt, letterpaper]{report}

% ── Márgenes ──
\usepackage[
  left   = 3cm,
  right  = 2.5cm,
  top    = 3cm,
  bottom = 2.5cm
]{geometry}

% ── Interlineado 1.5 ──
\usepackage{setspace}
\onehalfspacing

% ── Sin sangría, separación entre párrafos ──
\setlength{\parindent}{0pt}
\setlength{\parskip}{6pt}
```

---

## 2. Tipografía

| Elemento                          | Fuente           | Tamaño   | Estilo    |
|-----------------------------------|------------------|----------|-----------|
| Texto general                     | Times New Roman  | 12 pt    | Normal    |
| Títulos de sección (capítulo)     | Times New Roman  | 14 pt    | **Negrita** |
| Pie de figura / gráfica / foto   | Times New Roman  | 10 pt    | Normal, alineado a la izquierda del marco |
| Encabezado de tabla / cuadro      | Times New Roman  | 10 pt    | Normal, centrado respecto al marco |

```latex
% ── Fuente Times New Roman ──
\usepackage{mathptmx}          % Times para texto y matemáticas
\usepackage[T1]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage[spanish,es-tabla]{babel}

% ── Títulos de sección: 14pt negrita ──
\usepackage{titlesec}

\titleformat{\chapter}[display]
  {\normalfont\bfseries\fontsize{14}{17}\selectfont}
  {\chaptertitlename\ \thechapter}{12pt}
  {\fontsize{14}{17}\selectfont\bfseries}

\titleformat{\section}
  {\normalfont\bfseries\fontsize{14}{17}\selectfont}
  {\thesection}{1em}{}

\titleformat{\subsection}
  {\normalfont\bfseries\fontsize{12}{15}\selectfont}
  {\thesubsection}{1em}{}

% ── Cada capítulo inicia en hoja aparte (por defecto en report) ──
% report class ya hace \clearpage antes de cada \chapter.
```

---

## 3. Figuras, tablas y pies de página

```latex
\usepackage{graphicx}
\usepackage{float}
\usepackage{caption}
\usepackage{booktabs}

% ── Pie de figura: 10pt, alineado a la izquierda ──
\captionsetup[figure]{
  font        = {small},          % 10pt
  labelfont   = {bf},
  justification = raggedright,
  singlelinecheck = false,
  labelsep    = period,
  format      = hang
}

% ── Encabezado de tabla: 10pt, centrado ──
\captionsetup[table]{
  font        = {small},          % 10pt
  labelfont   = {bf},
  justification = centering,
  singlelinecheck = false,
  labelsep    = period,
  position    = top
}
```

---

## 4. Paginación

- Las páginas **preliminares** (portada, agradecimientos, resumen, índice) se numeran con **números romanos en minúsculas** (`\pagenumbering{roman}`) o **no se paginan**.
- La paginación **arábiga** (`\pagenumbering{arabic}`) inicia a partir de la **Introducción** (Capítulo 1).

```latex
% En el preámbulo, después de los preliminares:
\pagenumbering{roman}   % Preliminares (opcional, o sin paginación)

% Justo antes de la Introducción:
\clearpage
\pagenumbering{arabic}  % Inicia paginación en Introducción
```

---

## 5. Citas y referencias — Sistema Harvard-APA

```latex
\usepackage[
  backend  = biber,
  style    = apa,
  sorting  = nyt,
  language = spanish
]{biblatex}
\DeclareLanguageMapping{spanish}{spanish-apa}
\addbibresource{referencias.bib}

% Uso en texto:
% \textcite{autor2024}   → Autor (2024) describe que…
% \parencite{autor2024}  → …como se reporta (Autor, 2024).
```

---

## 6. Unidades — Sistema Internacional de Medidas (SIM)

```latex
\usepackage{siunitx}
\sisetup{
  output-decimal-marker = {.},
  group-separator       = {\,},
  per-mode              = symbol,
  locale                = US
}

% Ejemplos:
% \SI{25.4}{\milli\meter}       → 25.4 mm
% \SI{1500}{\kilo\gram}         → 1 500 kg
% \SI{100}{\degreeCelsius}      → 100 °C
```

---

## 7. Paquetes complementarios recomendados

```latex
\usepackage{hyperref}       % Hipervínculos internos y externos
\hypersetup{
  colorlinks  = true,
  linkcolor   = black,
  citecolor   = black,
  urlcolor    = blue,
  pdfauthor   = {Nombre del Autor},
  pdftitle    = {Título del Reporte de Residencia Profesional}
}

\usepackage{enumitem}       % Listas personalizadas
\usepackage{amsmath}        % Ecuaciones avanzadas
\usepackage{amssymb}        % Símbolos matemáticos
\usepackage{listings}       % Código fuente
\usepackage{xcolor}         % Colores
\usepackage{appendix}       % Anexos
\usepackage{pdfpages}       % Incluir PDFs (cartas de autorización)
\usepackage{tocloft}        % Personalizar índice
```

---

## 8. Estructura del documento (ITV-AC-PO-004-A02 Rev. 1)

El reporte **debe** seguir esta estructura exacta. Cada sección marcada como `\chapter` inicia en hoja aparte.

```latex
\begin{document}

% ═══════════════════════════════════════════
% PRELIMINARES (sin paginación arábiga)
% ═══════════════════════════════════════════
\pagenumbering{gobble}       % Sin número de página

% 1. Portada
\input{capitulos/portada}

\pagenumbering{roman}

% 2. Agradecimientos
\input{capitulos/agradecimientos}

% 3. Resumen
\input{capitulos/resumen}

% 4. Índice
\tableofcontents
\listoffigures
\listoftables

% ═══════════════════════════════════════════
% GENERALIDADES DEL PROYECTO
% ═══════════════════════════════════════════
\clearpage
\pagenumbering{arabic}

% 5. Introducción
\chapter{Introducción}
\input{capitulos/introduccion}

% 6. Descripción de la empresa
\chapter{Descripción de la empresa u organización y del puesto o área de trabajo del estudiante}
\input{capitulos/descripcion_empresa}

% 7. Problemas a resolver
\chapter{Problemas a resolver, priorizándolos}
\input{capitulos/problemas}

% 8. Objetivos
\chapter{Objetivos}
\input{capitulos/objetivos}
% Incluir: Objetivo General y Objetivos Específicos

% 9. Justificación
\chapter{Justificación}
\input{capitulos/justificacion}

% ═══════════════════════════════════════════
% MARCO TEÓRICO
% ═══════════════════════════════════════════

% 10. Marco Teórico
\chapter{Marco Teórico}
\input{capitulos/marco_teorico}

% ═══════════════════════════════════════════
% DESARROLLO
% ═══════════════════════════════════════════

% 11. Procedimiento y descripción de actividades
\chapter{Procedimiento y descripción de las actividades realizadas}
\input{capitulos/desarrollo}

% ═══════════════════════════════════════════
% RESULTADOS
% ═══════════════════════════════════════════

% 12. Resultados
\chapter{Resultados}
\input{capitulos/resultados}
% Incluir según aplique: planos, gráficas, prototipos, manuales,
% programas, análisis estadísticos, modelos matemáticos,
% simulaciones, normatividades, regulaciones y restricciones.
% Solo si aplica: estudio de mercado, estudio técnico, estudio económico.

% 13. Actividades Sociales (si aplica)
\chapter{Actividades Sociales realizadas en la empresa u organización}
\input{capitulos/actividades_sociales}

% ═══════════════════════════════════════════
% CONCLUSIONES
% ═══════════════════════════════════════════

% 14. Conclusiones
\chapter{Conclusiones, recomendaciones y experiencia profesional adquirida}
\input{capitulos/conclusiones}

% ═══════════════════════════════════════════
% COMPETENCIAS DESARROLLADAS
% ═══════════════════════════════════════════

% 15. Competencias desarrolladas
\chapter{Competencias desarrolladas y/o aplicadas}
\input{capitulos/competencias}

% ═══════════════════════════════════════════
% FUENTES DE INFORMACIÓN
% ═══════════════════════════════════════════

% 16. Fuentes de información
\printbibliography[title={Fuentes de información}]

% ═══════════════════════════════════════════
% ANEXOS
% ═══════════════════════════════════════════

\appendix

% 17. Anexos
\chapter{Anexos}
\input{capitulos/anexos}
% Incluir: Carta de autorización de la empresa para titulación, otros.

% 18. Registros de Productos (si aplica)
\chapter{Registros de Productos}
\input{capitulos/registros_productos}
% Patentes, derechos de autor, compra-venta del proyecto, etc.

\end{document}
```

---

## 9. Reglas de redacción (OBLIGATORIAS)

Toda generación de texto **debe** cumplir las siguientes reglas:

### 9.1 Persona y tiempo verbal
- Usar **forma impersonal** (tercera persona del singular).
  - ✅ `Se desarrolla un sistema que permite…`
  - ✅ `El proyecto consiste en…`
  - ❌ `Desarrollamos un sistema…`
  - ❌ `Desarrollé un sistema…`
- Usar **verbos en tiempo presente**.
  - ✅ `Se implementa…`, `Se obtiene…`, `Se analiza…`
  - ❌ `Se implementó…`, `Se obtuvo…`

### 9.2 Ortografía y estilo
- Cuidado estricto de la **ortografía** y **redacción**.
- Escribir con **mayúsculas y minúsculas** (no todo en mayúsculas, excepto donde se indique).
- No usar abreviaturas sin definir la primera vez.
- Usar **acentos y caracteres especiales** correctamente (`á, é, í, ó, ú, ñ, ü`).

### 9.3 Unidades de medida
- Usar **exclusivamente** el Sistema Internacional de Medidas (SIM).
- Emplear el paquete `siunitx` para consistencia tipográfica.

### 9.4 Citas y referencias
- Formato **Harvard-APA** usando `biblatex` con estilo `apa`.
- Toda afirmación que no sea del autor **debe** tener cita.
- Citas textuales de más de 40 palabras van en bloque con sangría.

```latex
% Cita textual larga (>40 palabras):
\begin{quote}
  Texto de la cita textual larga que excede las cuarenta palabras
  y debe presentarse en un bloque con sangría, sin comillas, con
  referencia al final \parencite[p.~45]{autor2024}.
\end{quote}
```

---

## 10. Convenciones de archivos del proyecto LaTeX

```
ReporteResis/
├── main.tex                    % Documento principal
├── referencias.bib             % Base de datos bibliográfica
├── GEMINI.md                   % Este archivo de instrucciones
├── capitulos/
│   ├── portada.tex
│   ├── agradecimientos.tex
│   ├── resumen.tex
│   ├── introduccion.tex
│   ├── descripcion_empresa.tex
│   ├── problemas.tex
│   ├── objetivos.tex
│   ├── justificacion.tex
│   ├── marco_teorico.tex
│   ├── desarrollo.tex
│   ├── resultados.tex
│   ├── actividades_sociales.tex
│   ├── conclusiones.tex
│   ├── competencias.tex
│   ├── anexos.tex
│   └── registros_productos.tex
├── figuras/                    % Imágenes y gráficas
│   └── logo_itv.png
└── tablas/                     % Datos tabulares (si aplica)
```

---

## 11. Plantilla base completa (`main.tex`)

Al crear `main.tex` por primera vez, usar esta plantilla completa:

```latex
% ══════════════════════════════════════════════════════════════
% Reporte Final de Residencia Profesional
% Tecnológico Nacional de México / Instituto Tecnológico de Veracruz
% ITV-AC-PO-004-A02 Rev. 1
% ══════════════════════════════════════════════════════════════

\documentclass[12pt, letterpaper]{report}

% ── Geometría ──
\usepackage[left=3cm, right=2.5cm, top=3cm, bottom=2.5cm]{geometry}

% ── Interlineado ──
\usepackage{setspace}
\onehalfspacing

% ── Sin sangría ──
\setlength{\parindent}{0pt}
\setlength{\parskip}{6pt}

% ── Tipografía ──
\usepackage{mathptmx}
\usepackage[T1]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage[spanish,es-tabla]{babel}

% ── Títulos ──
\usepackage{titlesec}
\titleformat{\chapter}[display]
  {\normalfont\bfseries\fontsize{14}{17}\selectfont}
  {\chaptertitlename\ \thechapter}{12pt}
  {\fontsize{14}{17}\selectfont\bfseries}
\titleformat{\section}
  {\normalfont\bfseries\fontsize{14}{17}\selectfont}
  {\thesection}{1em}{}
\titleformat{\subsection}
  {\normalfont\bfseries\fontsize{12}{15}\selectfont}
  {\thesubsection}{1em}{}

% ── Figuras y tablas ──
\usepackage{graphicx}
\usepackage{float}
\usepackage{caption}
\usepackage{booktabs}
\captionsetup[figure]{
  font=small, labelfont=bf,
  justification=raggedright,
  singlelinecheck=false,
  labelsep=period, format=hang
}
\captionsetup[table]{
  font=small, labelfont=bf,
  justification=centering,
  singlelinecheck=false,
  labelsep=period, position=top
}

% ── Unidades SI ──
\usepackage{siunitx}
\sisetup{
  output-decimal-marker={.},
  group-separator={\,},
  per-mode=symbol
}

% ── Bibliografía APA ──
\usepackage[backend=biber, style=apa, sorting=nyt, language=spanish]{biblatex}
\DeclareLanguageMapping{spanish}{spanish-apa}
\addbibresource{referencias.bib}

% ── Otros ──
\usepackage{hyperref}
\hypersetup{
  colorlinks=true, linkcolor=black,
  citecolor=black, urlcolor=blue
}
\usepackage{enumitem}
\usepackage{amsmath, amssymb}
\usepackage{listings}
\usepackage{xcolor}
\usepackage{appendix}
\usepackage{pdfpages}
\usepackage{tocloft}

% ══════════════════════════════════════════════════════════════
\begin{document}

% --- Preliminares ---
\pagenumbering{gobble}
\input{capitulos/portada}

\pagenumbering{roman}
\input{capitulos/agradecimientos}
\input{capitulos/resumen}

\tableofcontents
\listoffigures
\listoftables

% --- Cuerpo del reporte ---
\clearpage
\pagenumbering{arabic}

\chapter{Introducción}
\input{capitulos/introduccion}

\chapter{Descripción de la empresa u organización y del puesto o área de trabajo del estudiante}
\input{capitulos/descripcion_empresa}

\chapter{Problemas a resolver, priorizándolos}
\input{capitulos/problemas}

\chapter{Objetivos}
\input{capitulos/objetivos}

\chapter{Justificación}
\input{capitulos/justificacion}

\chapter{Marco Teórico}
\input{capitulos/marco_teorico}

\chapter{Procedimiento y descripción de las actividades realizadas}
\input{capitulos/desarrollo}

\chapter{Resultados}
\input{capitulos/resultados}

\chapter{Actividades Sociales realizadas en la empresa u organización}
\input{capitulos/actividades_sociales}

\chapter{Conclusiones, recomendaciones y experiencia profesional adquirida}
\input{capitulos/conclusiones}

\chapter{Competencias desarrolladas y/o aplicadas}
\input{capitulos/competencias}

% --- Fuentes de información ---
\printbibliography[title={Fuentes de información}]

% --- Anexos ---
\appendix
\chapter{Anexos}
\input{capitulos/anexos}

\chapter{Registros de Productos}
\input{capitulos/registros_productos}

\end{document}
```

---

## 12. Checklist de validación antes de compilar

- [ ] Tamaño de papel: `letterpaper`
- [ ] Márgenes: izq 3cm, der 2.5cm, sup 3cm, inf 2.5cm
- [ ] Interlineado: 1.5
- [ ] Fuente: Times New Roman (mathptmx), 12pt
- [ ] Títulos: 14pt, negrita
- [ ] Sin sangría (`\parindent = 0pt`)
- [ ] Paginación arábiga inicia en Introducción
- [ ] Cada capítulo inicia en hoja aparte
- [ ] Pies de figura: 10pt, alineados a la izquierda
- [ ] Encabezados de tabla: 10pt, centrados
- [ ] Citas y referencias en formato Harvard-APA
- [ ] Unidades en SIM con `siunitx`
- [ ] Redacción impersonal en tiempo presente
- [ ] Ortografía y acentuación correctas
- [ ] Estructura completa según ITV-AC-PO-004-A02 Rev. 1
