\documentclass[runningheads]{article}

% Ajuste de márgenes para asemejar el diseño de página de LLNCS (12.2cm de ancho x 19.3cm de alto)
\usepackage[a4paper, total={122mm,193mm}, centering]{geometry}
\usepackage[utf8]{inputenc}
\usepackage[spanish]{babel}
\usepackage{listings}
\usepackage{xcolor}
\usepackage{titlesec}
\usepackage{amsmath}

% Tipografía aproximada al estilo Times Roman de LLNCS
\usepackage{mathptmx}

% Configuración de colores para los bloques de código
\definecolor{codegreen}{rgb}{0,0.6,0}
\definecolor{codegray}{rgb}{0.5,0.5,0.5}
\definecolor{codepurple}{rgb}{0.58,0,0.82}
\definecolor{backcolor}{rgb}{0.95,0.95,0.92}

\lstdefinestyle{mystyle}{
    backgroundcolor=\color{backcolor},   
    commentstyle=\color{codegreen},
    keywordstyle=\color{magenta},
    numberstyle=\tiny\color{codegray},
    stringstyle=\color{codepurple},
    basicstyle=\ttfamily\footnotesize,
    breakatwhitespace=false,         
    breaklines=true,                 
    captionpos=b,                    
    keepspaces=true,                 
    numbers=left,                    
    numbersep=5pt,                  
    showspaces=false,                
    showstringspaces=false,
    showtabs=false,                  
    tabsize=2
}
\lstset{style=mystyle}

% Formateo de títulos al estilo LLNCS
\titleformat{\section}{\normalfont\large\bfseries}{\thesection}{1em}{}
\titleformat{\subsection}{\normalfont\normalsize\bfseries}{\thesubsection}{1em}{}
\titleformat{\subsubsection}[runin]{\normalfont\normalsize\bfseries}{\thesubsubsection}{1em}{}[.]

\begin{document}

\title{Explicación de la Herramienta Posit Cloud}
\author{Simón Fischer \and Rubén Cruz \and Yésica Villaca \and Chiara Palmero \and Matías Rosa}
\date{}

\maketitle

\begin{center}
\vspace{-2em}
{\small Universidad Nacional de Cuyo, Instituto de Ingeniería Industrial}
\end{center}

\vspace{2em}

\section{Los Componentes de la Interfaz (Los 4 Paneles)}
RStudio organiza el espacio de trabajo en cuatro áreas principales. Entender qué hace cada una es fundamental:

\begin{itemize}
    \item \textbf{El Editor de Scripts (Arriba a la izquierda):} Es tu bloc de notas inteligente. Aquí escribís y guardás tus archivos de código (\texttt{.R}), documentos R Markdown (\texttt{.Rmd}) o archivos de Quarto (\texttt{.qmd}). El código escrito acá no se ejecuta hasta que vos se lo ordenás.
    \item \textbf{La Consola (Abajo a la izquierda):} Es el motor de R. Aquí se ejecuta el código en tiempo real y se muestran los resultados inmediatos de tus operaciones. Podés escribir comandos directos al lado del símbolo \texttt{">"}, pero lo que escribas acá no se guardará en ningún archivo al cerrar la sesión.
    \item \textbf{El Entorno de Trabajo (Environment - Arriba a la derecha):} Es la memoria visual de tu sesión. Cada vez que creás una variable, cargás un dataset (base de datos) o guardás un vector, aparecerá listado acá con su nombre, tipo y dimensiones.
    \item \textbf{El Panel de Utilidades (Abajo a la derecha):} Contiene varias pestañas críticas:
    \begin{itemize}
        \item \emph{Files:} El explorador de archivos de tu computadora virtual en la nube.
        \item \emph{Plots:} Donde se muestran los gráficos estáticos que generás.
        \item \emph{Packages:} Tu biblioteca de herramientas (ver qué tenés instalado y activarlo).
        \item \emph{Help:} El manual de auxilio integrado.
    \end{itemize}
\end{itemize}

\section{Cómo Insertar y Ejecutar Código}
Para trabajar en el Editor de Scripts de forma eficiente, existen combinaciones de teclas que agilizan el flujo de trabajo:

\begin{itemize}
    \item \textbf{Insertar código:} Escribís tus funciones directamente en el script. Podés usar comentarios anteponiendo el símbolo \texttt{"\#"} para que R ignore esa línea y te sirva de anotación personal.
    \item \textbf{Ejecutar una línea o selección:} Colocás el cursor sobre la línea de código que querés correr y presionás \texttt{Ctrl + Enter} (en Windows) o \texttt{Cmd + Enter} (en Mac). El código se enviará automáticamente a la Consola para ejecutarse.
    \item \textbf{Insertar el operador de asignación (\texttt{<-}):} En lugar de escribir el signo ``menos'' y el ``menor que'', podés presionar \texttt{Alt + -} (en Windows) u \texttt{Option + -} (en Mac) y RStudio lo escribirá por vos con los espacios correctos.
\end{itemize}

\section{El Sistema de Ayuda (Help)}
R tiene una de las documentaciones más completas, y podés acceder a ella sin salir de Posit Cloud. Te muestra la descripción de la función, qué argumentos recibe y ejemplos de uso al final de la página.

\begin{itemize}
    \item \textbf{Uso desde la Consola:} Si querés saber cómo funciona la herramienta \texttt{boxplot}, escribís en la consola \texttt{?boxplot} o \texttt{help(boxplot)} y presionás Enter. La documentación se abrirá en la pestaña Help (abajo a la derecha).
    \item \textbf{Búsqueda manual:} Podés ir directo a la pestaña Help, escribir el nombre de cualquier función en la barra de búsqueda con el ícono de la lupa y presionar Enter.
\end{itemize}

\section{Gestión y Descarga de Paquetes (Packages)}
R base viene con funciones esenciales, pero para análisis avanzados necesitás ``paquetes'' (cajas de herramientas creadas por la comunidad).

\begin{itemize}
    \item \textbf{Instalación (Descarga):} Se usa el comando \texttt{install.packages('nombre\_del\_paquete')} en la consola. En Posit Cloud esto se conecta a servidores optimizados que descargan versiones precompiladas para Linux en segundos. Esto se hace una sola vez por proyecto.
    \item \textbf{Activación (Abrir la caja):} Para usar las funciones de un paquete instalado en tu script, debés llamarlo al inicio de tu código usando \texttt{library(nombre\_del\_paquete)} (esta vez sin comillas). Esto se debe hacer cada vez que abrís tu proyecto.
\end{itemize}

\section{Herramientas de Comparación de Rendimiento (Benchmarking)}
Cuando estás programando simulaciones, algoritmos matemáticos o sumatorias, a veces existen diferentes formas de resolver el mismo problema (por ejemplo, usar un bucle \texttt{for} versus usar funciones vectorizadas). Para medir qué camino es más rápido y eficiente, RStudio cuenta con herramientas de benchmarking.

\begin{lstlisting}[language=R, caption={Ejemplo de uso de microbenchmark en RStudio.}]
# Paso 1: Instalacion del paquete (ejecutar solo una vez si no esta instalado)
# install.packages("microbenchmark")

# Paso 2: Carga de la libreria
library(microbenchmark)

# Definicion de funciones de ejemplo para la simulacion
para_cada_elemento <- function() {
  # (Espacio para el codigo basado en bucles)
}

operacion_directa <- function() {
  # (Espacio para el codigo vectorizado optimizado)
}

# Paso 3: Comparacion de opciones ejecutando el benchmark
resultado <- microbenchmark(
  opcion_bucle  = para_cada_elemento(),
  opcion_vector = operacion_directa(),
  times = 100
)

# Paso 4: Visualizacion de los resultados detallados en la consola
print(resultado)
\end{lstlisting}

\section{La Terminal del Sistema: El Aliado Oculto}
Al lado de la pestaña de la Consola, vas a encontrar una pestaña llamada ``Terminal''. Esta no es la consola de R, sino una terminal de comandos Linux (el sistema operativo que corre detrás de Posit Cloud).

Te sirve para tareas que están por fuera de R, como por ejemplo interactuar con GitHub usando comandos tradicionales de Git (\texttt{git add}, \texttt{git commit}, \texttt{git push}), administrar carpetas ocultas del sistema o instalar herramientas complementarias.

\vspace{2em}

\end{document}
