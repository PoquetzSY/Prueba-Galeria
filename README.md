# Prueba Galeria

Galería de imágenes de Rick & Morty creada para la evaluación de habilidades en HTML, CSS, JavaScript, APIs y Git.

## Características

- Carrusel de imagenes.
- Visualización de imágenes en una cuadrícula.
- Diseño responsive que se adapta a diferentes tamaños de pantalla.
- La paleta de colores de la galeria esta basada en Rick Sanchez: https://color.adobe.com/es/-Sanchez-color-theme-7039684/

## Tecnologías Utilizadas

- Vue 3
- Vite
- Tailwind CSS
- Vue3-Carousel
- Vue3-spinners
- Rick and Morty API

## Instalación

1. Clona este repositorio:
  ```bash
  git clone https://github.com/PoquetzSY/Prueba-Galeria.git
  ```
2. Navega al directorio del proyecto:
  ```bash
  cd Prueba-Galeria
  ```
3. Instala las dependencias:
  ```bash
  npm install
  ```
4. Inicia el servidor de desarrollo:
  ```bash
  npm run dev
  ```

## Uso

1. La aplicación realiza el fetch de información desde la API de Rick and Morty.
2. La información obtenida por la API se encuentra paginada por la misma API, por lo que si deseas ver más datos de tendras que modificar los params que se envian al endpoint, En la documentación de la API explican los parametros de consulta para el endpoint para obtener más datos mediante la paginación: https://rickandmortyapi.com/documentation/#info-and-pagination
