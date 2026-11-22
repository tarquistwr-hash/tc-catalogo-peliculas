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

*(Pendiente: se completará al final del proyecto.)*