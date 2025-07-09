# Instalación de plotly
install.packages("plotly")
install.packages("ggthemes")
install.packages("ggplot")
# Instalación de DT
install.packages("DT")

install.packages("scales")

install.packages("ggplot2")
install.packages("hrbrthemes")

# Carga conjunta de Tidyverse 
# (incluye ggplot2, dplyr, readr y otros)
library(tidyverse)

# Carga de plotly
library(plotly)

# Carga de DT
library(DT)

# Carga de scales (para formatear ejes y leyendas en los gráficos)
library(scales)
library(hrbrthemes)
library(ggthemes)
library(ggplot)



paises <- read.csv("https://raw.githubusercontent.com/sigenr/2025-i/refs/heads/main/datos/natural-earth/paises.csv")


# Tabla de datos de paises
paises |> DT::datatable(
  options = list(
    pageLength = 5,
    language = list(url = '//cdn.datatables.net/plug-ins/1.10.11/i18n/Spanish.json')
  )
)

# Gráfico de dispersión de PIB per cápita vs esperanza de vida al nacer
# coloreado por continente
paises |>
  ggplot(aes(x = GDP_PC, y = LIFE_EXPECTANCY, color = CONTINENT)) +
  geom_point() +
  scale_x_continuous(labels = comma, limits = c(0, NA))


