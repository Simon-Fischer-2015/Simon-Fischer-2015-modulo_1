# ==============================================================================
# SCRIPT DE RENDIMIENTO: BUCLES VS VECTORIZACIÓN EN R
# Autores: Grupo Alfa
# Instituto de Ingeniería Industrial - UNCuyo
# ==============================================================================

# ---- 1. INSTALACIÓN Y CARGA DE PAQUETES ----
# Detecta si el paquete está instalado; si no, lo instala automáticamente
if (!requireNamespace("microbenchmark", quietly = TRUE)) {
  install.packages("microbenchmark")
}
if (!requireNamespace("ggplot2", quietly = TRUE)) {
  install.packages("ggplot2")
}

library(microbenchmark)
library(ggplot2)

# ---- 2. DEFINICIÓN DE FUNCIONES A COMPARAR ----
# Supongamos que queremos calcular el cuadrado de cada elemento en un vector pesado

# Opción A: Usando un bucle for tradicional (itera elemento por elemento)
calcular_con_bucle <- function(datos) {
  resultado <- numeric(length(datos))
  for (i in 1:length(datos)) {
    resultado[i] <- datos[i]^2
  }
  return(resultado)
}

# Opción B: Usando operaciones vectorizadas nativas de R (optimizado)
calcular_vectorizado <- function(datos) {
  return(datos^2)
}

# ---- 3. PREPARACIÓN DE LOS DATOS DE PRUEBA ----
# Creamos un vector con 50.000 observaciones (simulando una medición industrial)
set.seed(42)
muestras_produccion <- runif(50000, min = 10, max = 500)

# ---- 4. EJECUCIÓN DEL BENCHMARK ----
cat("Iniciando la comparación de rendimiento (100 repeticiones)...\n")

tabla_rendimiento <- microbenchmark(
  bucle_for   = calcular_con_bucle(muestras_produccion),
  vectorizado = calcular_vectorizado(muestras_produccion),
  times = 100
)

# ---- 5. VISUALIZACIÓN DE RESULTADOS ----
# Imprime las métricas en la consola (mínimo, media, mediana, máximo)
print(tabla_rendimiento)

# Genera un gráfico de cajas (boxplot) para comparar los tiempos de ejecución
cat("\nGenerando gráfico de tiempos de procesamiento...\n")
grafico <- autoplot(tabla_rendimiento) +
  labs(
    title = "Comparación de Tiempos de Procesamiento",
    subtitle = "Bucle For vs. Operación Vectorizada Nativa",
    x = "Expresión Evaluada",
    y = "Tiempo (Nanosegundos / Milisegundos)"
  ) +
  theme_minimal()

# Muestra el gráfico en pantalla
print(grafico)
