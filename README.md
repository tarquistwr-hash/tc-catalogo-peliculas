# Catálogo de películas · Team Challenge

**Equipo:** Alejandro Tarquis, Teodulo Mba Obono, Jesús Moradillo

Catálogo de películas enriquecido a partir del dataset MovieLens: análisis con Pandas, sinopsis y web oficial desde la API de TMDB, y sinopsis en español generadas con Gemini.

## Reparto de funciones

| Persona | Rol | Notebook / tarea | Revisa PRs de |
|---|---|---|---|
| Alejandro Tarquis | A · Repo y datos | `01_ingesta_limpieza` + apartado 5 de `02_analisis` (preguntas). Repo, ramas, README y PR final `develop` → `main` | Teodulo |
| Teodulo Mba Obono | B · Análisis | `02_analisis`, apartados 3–4 (merge y agregaciones). Calidad del código y prueba de reproducibilidad | Jesús |
| Jesús Moradillo | C · APIs e IA generativa | `03_tmdb` y `04_gemini`. Gestión de claves y `.env.example` | Tarquis |

## Instalación

```bash
git clone https://github.com/tarquistwr-hash/tc-catalogo-peliculas.git
cd tc-catalogo-peliculas
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env            # Windows: copy .env.example .env  — y rellenad las claves
```

## Claves necesarias

| Variable | Dónde se obtiene |
|---|---|
| `TMDB_READ_ACCESS_TOKEN` o `TMDB_API_KEY` | themoviedb.org → Settings → API |
| `GEMINI_API_KEY` | aistudio.google.com |

El fichero `.env` está en `.gitignore`: **nunca se sube al repositorio**.

## Ejecución

Ejecutad los notebooks **en este orden** (cada uno genera un CSV en `data/processed/` que usa el siguiente):

1. `01_ingesta_limpieza.ipynb` → `movies_clean.csv`
2. `02_analisis.ipynb`
3. `03_tmdb.ipynb` → `movies10.csv`
4. `04_gemini.ipynb` → `movies10_es.csv`

## Resultados principales

- **Limpieza:** 9742 películas. Se extrajo el año del título en una columna `year`; 13 películas no tienen año reconocible (una de ellas con un rango de años, *Death Note (2006–2007)*).
- **Merge:** al unir valoraciones y etiquetas con las películas no se pierde ni se duplica ninguna fila. Hay 18 películas sin ninguna valoración.
- **Segmentación:** los usuarios con menos de 100 valoraciones dan de media notas algo más altas (3,71) que los que valoran mucho (3,58).
- **Preguntas:** hay 279 películas de los años 50 y 306 que son a la vez Sci-Fi y Adventure. La tag más repetida, *In Netflix queue*, no describe la película: es una nota personal del usuario.
- **TMDB y Gemini:** se obtuvieron la sinopsis y la web oficial de 10 películas (6 no tienen web oficial) y Gemini generó un resumen en español de las 10.