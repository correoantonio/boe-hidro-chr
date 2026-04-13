# BOE Hidro CHR — Live Intelligence

> Rastreador en vivo del Boletín Oficial del Estado orientado a proyectos de **centrales hidroeléctricas reversibles (CHR)**, dominio público hidráulico y permitting en confederaciones hidrográficas españolas.

[![Demo en vivo](https://img.shields.io/badge/Demo-Live-brightgreen?style=for-the-badge)](https://antonio-rueda-caballero.github.io/boe-hidro-chr)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Antonio%20Rueda-0077B5?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/antonio-rueda-caballero-21665323b)
[![Versión pro](https://img.shields.io/badge/Versión%20pro-Solicitar-F6C90E?style=for-the-badge)](mailto:antonio.rueda.caballero@gmail.com?subject=Solicitud%20versión%20escritorio%20BOE%20Hidro%20CHR)

---

## ¿Qué hace?

La herramienta conecta directamente con la **API oficial del BOE** (`datosabiertos.boe.es`) desde el navegador, filtra los anuncios relevantes para el sector hidroeléctrico y los presenta en un dashboard interactivo con scoring, agrupación por expediente y timeline administrativo.

**Sin servidores. Sin instalación. Un único archivo HTML.**

---

## Capacidades

| Módulo | Detalle |
|---|---|
| 🔍 **Scraping en vivo** | Llama directamente a la API REST del BOE por día. Concurrencia configurable (1–12 workers), retry con backoff, deduplicación por identidad compuesta |
| 🧠 **Scoring CHR** | 4 perfiles de scoring (Balanceado CHR, Agua/DPH, Permitting, Licitaciones). Evalúa título + texto del anuncio + tipo + fase administrativa |
| 📁 **Expedientes** | Agrupación automática por código formal (A/20/…) o huella combinada (promotor + río + municipio + tipo). Filtros por CHR, score, búsqueda libre |
| 📅 **Timeline interactivo** | Visualización horizontal del ciclo de vida completo de cada expediente. Flechas de navegación. Abre el anuncio original con un clic |
| 📊 **Dashboard analítico** | 4 gráficos interactivos (año, bloque funcional, tipo, fase de permitting). Pulsar una barra filtra el listado al instante |
| 📥 **Carga de CSV previo** | Importa resultados de búsquedas anteriores para análisis offline sin esperar nuevo scraping |
| 💾 **Persistencia local** | Configuración y resultados guardados en `localStorage`. La sesión se recupera automáticamente al reabrir |
| 📤 **Export CSV / JSON** | Formato compatible para reutilizar en Excel, Power BI o en la propia herramienta |
| 📱 **Responsive** | Funciona en escritorio, tablet y móvil (iOS Safari incluido) |

---

## Confederaciones y fuentes soportadas

| Organismo | Fuente |
|---|---|
| CH Cantábrico, Duero, Ebro, Guadalquivir, Guadiana, Júcar, Miño-Sil, Segura, Tajo, Norte | BOE |
| Augas de Galicia | DOG |
| Todas a la vez | BOE (modo lento, no recomendable para rangos largos) |

---

## Uso rápido

1. Abre la [demo en vivo](https://antonio-rueda-caballero.github.io/boe-hidro-chr) — o descarga `index.html` y ábrelo localmente
2. Selecciona la **confederación** y el **rango de años**
3. Ajusta las **keywords** y el **perfil de scoring** según tu interés
4. Pulsa **▶ Iniciar búsqueda**
5. Los resultados se acumulan en tiempo real en el dashboard

O bien pulsa **Demo** para explorar la interfaz con datos de ejemplo sin esperar.

---

## Scoring CHR — ¿cómo funciona?

El score (0–100) se calcula combinando:

- **Términos en título** — `reversible`, `bombeo`, `competencia de proyectos`, `aprovechamiento`, `salto`…
- **Términos en cuerpo** — `pumped storage`, `central reversible`, `dominio público hidráulico`…
- **Tipo de anuncio** — competencia de proyectos y concesiones puntúan más alto
- **Fase administrativa** — `Competencia` y `Concesión DPH` son las fases de mayor interés para CHR
- **Trazas terminológicas** — `embalse`, `balsa`, `turbinado`, `caudal`, línea de evacuación

```
Score ≥ 70  →  Alta prioridad  (verde)
Score ≥ 45  →  Interés medio   (teal)
Score < 45  →  Base            (azul)
```

---

## Extracción de metadatos

La herramienta extrae automáticamente del título del anuncio:

- **Promotor** — forma jurídica (S.L., S.A., S.L.U.), Comunidad de Regantes, Ayuntamiento, persona física, organismos energéticos conocidos (Iberdrola, Endesa, Acciona, Naturgy, EDP…)
- **Municipio** — término municipal, múltiples municipios, provincia en paréntesis
- **Río / corriente** — río, arroyo, embalse, canal, torrente, rambla, barranco
- **Expediente** — código formal tipo `A/20/2º1401` o huella combinada cuando no existe

---

## Estructura del repositorio

```
boe-hidro-chr/
├── index.html        # Aplicación completa (HTML + CSS + JS en un único archivo)
└── README.md         # Este archivo
```

No hay dependencias externas, frameworks ni build steps. Todo funciona abriendo `index.html`.

---

## Versión profesional de escritorio

Esta herramienta web es una **demo pública** de un sistema más completo que incluye:

- ⚙️ Automatización diaria programada (sin mantener el navegador abierto)
- 🔔 Alertas por email o Telegram al detectar nuevos anuncios relevantes
- 🗄️ Base de datos histórica con backfill desde 2005
- 📡 Integración con DOG, BOJA, DOGV y otros boletines autonómicos
- 📊 Dashboard Power BI / Excel con actualización automática
- 🔗 API REST para integración con otros sistemas

**¿Te interesa la versión pro?**
Escríbeme a [antonio.rueda.caballero@gmail.com](mailto:antonio.rueda.caballero@gmail.com?subject=Solicitud%20versión%20escritorio%20BOE%20Hidro%20CHR) o conéctate en [LinkedIn](https://www.linkedin.com/in/antonio-rueda-caballero-21665323b).

---

## Autor

**Antonio Rueda Caballero**
Especialista en proyectos de energía renovable e infraestructuras hidráulicas.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Conectar-0077B5?style=flat&logo=linkedin)](https://www.linkedin.com/in/antonio-rueda-caballero-21665323b)
[![Email](https://img.shields.io/badge/Email-Contactar-EA4335?style=flat&logo=gmail)](mailto:antonio.rueda.caballero@gmail.com)

---

## Licencia

© Antonio Rueda Caballero. Todos los derechos reservados.

Los datos provienen de la [API oficial del BOE](https://www.boe.es/datosabiertos/) bajo licencia de reutilización de la Agencia Estatal BOE.
