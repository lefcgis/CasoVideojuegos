# Insights del Mundo de Videojuegos
**Maestría en Business Analytics e Inteligencia Artificial — Proyecto de Investigación I**  
*Miguel Ángel Patiño Antoniou · Joel Apolaya · Eduardo Cabrera · Luis Ferrer · Rossangélica Gutiérrez · Francisco Vela*  
*Universidad Nacional de Ingeniería*  

---

## Presentación general

Este proyecto analiza el mercado global de videojuegos físicos desde 1980 hasta 2016 a través de datos históricos de ventas por plataforma, género y región. El objetivo es extraer patrones accionables que permitan tomar decisiones estratégicas de negocio fundamentadas en evidencia. La presentación destaca por su diseño temático: fondo visual al estilo *Street Fighter II*, lo que refleja coherencia entre el objeto de estudio y la forma de comunicarlo —un detalle estético que suma al impacto narrativo.

---

## Hallazgo 1 — Dominio geográfico: Norteamérica y Europa mandan

**Dato clave:** Norteamérica concentra aproximadamente el 45 % de las copias físicas vendidas globalmente, Europa el 30 % y Japón el 15 %. El resto del mundo representa un porcentaje marginal.

**Valoración:** La distribución geográfica es altamente asimétrica. NA y EU no solo son los mercados más grandes, sino los más interdependientes (como se confirmará con el análisis de correlación). Esto implica que una estrategia de lanzamiento que no priorice estos dos mercados simultáneamente está dejando ingresos sobre la mesa desde el día uno.

---

## Hallazgo 2 — Géneros dominantes en ventas globales

| Género | Ventas globales (M) |
|---|---|
| Action | 1,751.2 |
| Sports | 1,330.9 |
| Shooter | 1,037.4 |
| Role-Playing | 927.4 |
| Platform | 831.4 |
| Misc | 810.0 |
| Racing | 732.0 |
| Fighting | 448.9 |
| Simulation | 392.2 |
| Puzzle | 244.9 |
| Adventure | 239.0 |
| Strategy | 175.1 |

**Dato clave:** Los géneros Acción, Deportes y Disparos concentran el 55 % de las copias físicas vendidas entre 1980 y 2016.

**Valoración:** La concentración en tres géneros es una señal de mercado poderosa pero también una advertencia: el volumen de ventas en esos géneros está altamente vinculado al *hype* y a ciclos de hardware. Las apuestas por géneros de nicho (RPG, Simulación) pueden ser más defensivas ante la volatilidad. Además, el relativamente alto volumen de "Misc" (juegos no clasificados) sugiere que los datos tienen ruido categorial, lo que podría distorsionar levemente los rankings reales.

---

## Hallazgo 3 — Evolución temporal: auge y caída del físico

El gráfico de ventas globales por año muestra una curva en forma de campana muy pronunciada:

- **1980–1994:** crecimiento lento y volátil (~11M a ~88M)
- **1995–2008:** explosión sostenida, de ~200M hasta el pico de **678.9M en 2008**
- **2009–2016:** caída abrupta hasta prácticamente **0.1M en 2017 y 0.3M en 2020**

**Valoración:** La caída no es solo cíclica —es estructural. El desplome post-2008 coincide con la masificación del digital (Steam, PSN, Xbox Live), el auge del *free-to-play* y las plataformas móviles. El dato de 2017–2020 (~0M) casi con certeza refleja el límite del dataset (exclusivo de ventas físicas y de ciertos minoristas), no la desaparición real del mercado. Aun así, la tendencia es inequívoca: el físico como canal primario está en declive irreversible. Este hallazgo es el contexto que da urgencia a todas las recomendaciones estratégicas.

---

## Hallazgo 4 — Plataformas en Japón vs. el Resto del Mundo

El ranking de plataformas por JP_Sales revela que los 5 primeros puestos son portátiles o consolas de sobremesa japonesas:

1. DS — 175M
2. PS — 139.8M
3. PS2 — 137.5M
4. SNES — 116.5M
5. NES — 98.7M
6. 3DS — 97.3M

Las portátiles (DS, 3DS, PSP, GBA) representan más del 50 % del top-20 en ventas japonesas.

**Valoración:** Japón no sigue el mismo modelo de consumo que Occidente. La preferencia por portátiles sugiere patrones culturales y de movilidad distintos (largas horas en transporte público, cultura del *pick-up-and-play*). Ignorar esta diferencia y lanzar solo versiones de consola doméstica en ese mercado es una estrategia subóptima. La baja correlación de JP_Sales con ventas globales (≤0.40) confirma que Japón debe tratarse como un segmento con su propia hoja de ruta.

---

## Hallazgo 5 — Impacto regional en las plataformas más populares

Las 6 plataformas con mayor volumen total (PS2, X360, PS3, Wii, DS, PS) muestran patrones regionales distintos:

| Plataforma | Total (M) | NA | EU | JP | Other |
|---|---|---|---|---|---|
| PS2 | 1,256 | 584 | 339 | 139 | 193 |
| X360 | 980 | 601 | 281 | 12 | 86 |
| PS3 | 958 | 392 | 344 | 80 | 142 |
| Wii | 926 | 508 | 268 | 69 | 81 |
| DS | 821 | 391 | 195 | 176 | 61 |
| PS | 731 | 337 | 214 | 140 | 41 |

**Valoración:** El X360 es notablemente norteamericano (601M NA vs. solo 12M JP), mientras que el DS tiene una distribución más equilibrada gracias a su penetración japonesa. El PS2, con 1,256M totales, sigue siendo el hardware más vendido de la historia en este dataset —un punto de referencia para entender el impacto de un lanzamiento verdaderamente global. La distribución del PS3 (344M EU vs 392M NA) muestra que Europa puede casi parear a NA en plataformas con buena penetración, lo que refuerza la lógica del lanzamiento sincronizado NA+EU.

---

## Hallazgo 6 — Correlaciones entre regiones

El heatmap de correlaciones revela:

- **NA_Sales ↔ Global_Sales:** correlación muy alta (~0.95)
- **EU_Sales ↔ Global_Sales:** correlación alta (~0.90, R confirmado en scatter)
- **JP_Sales ↔ Global_Sales:** correlación moderada-baja (~0.40)
- **JP_Sales ↔ NA_Sales / EU_Sales:** correlación débil

**Valoración:** La correlación de 0.90 entre ventas en EU y ventas globales (con cada 1M en EU ≈ 2.6M globales) es uno de los hallazgos más accionables del análisis. Permite construir un **modelo bivariado NA+EU** con alta precisión predictiva para estimar el desempeño global de un título antes de expandir a otros mercados. La baja correlación de Japón con el resto del mundo no implica que sea un mercado poco rentable, sino que requiere una estrategia completamente diferenciada.

---

## Recomendaciones estratégicas (10 palancas)

### Palancas 1–5

| # | Palanca | Evidencia | Decisión estratégica | KPI |
|---|---|---|---|---|
| 1 | **Acción inmediata en NA + EU** | Correlación ≥0.85 con ventas globales; 1M EU ≈ 2.6M globales | Lanzamientos *day-one* sincronizados NA/EU; refuerzo de servidores y logística en las primeras 72h | Attach-rate día 7 / Retención D30 |
| 2 | **Localización premium para Japón** | JP_Sales correlación ≤0.40; preferencia por portátiles | Versiones portátiles/híbridas (Switch, Mobile); doblaje y arte exclusivo JRPG | % usuarios JP activos/mes / Ratio compras in-app |
| 3 | **Experiencia "pick-up-and-play"** | Portátiles = +50 % del top-20 JP | Modos rápidos y guardado instantáneo en AAA occidentales; cross-save cloud | Tiempo medio de sesión <10 min / % partidas retomadas |
| 4 | **Contenido vivo y social** | Acción-Sports-Shooter = 55 % de ventas, pero dependen de hype | Live-Ops semanales (eventos, skins, torneos); chat, clanes y recompensas comunitarias | DAU/MAU / ARPPU eventos |
| 5 | **Nostalgia monetizable** | NES/SNES aún mueven >200M por reediciones | Retro Bundles con filtros HD y logros sociales; Legacy Pass anual con catálogo creciente | Tasa de conversión Legacy Pass / Churn retro |

### Palancas 6–10

| # | Palanca | Evidencia | Decisión estratégica | KPI |
|---|---|---|---|---|
| 6 | **Pricing dinámico & accesibilidad** | Mercados "Other" siguen hits occidentales pero con menor poder adquisitivo | Precios regionales en digital; paquetes Lite (DLC opcional); prueba gratuita de 3h con guardado persistente | CAGR ventas "Other" / Ratio upgrade Lite→Full |
| 7 | **Analítica en tiempo real** | Alto solapamiento NA/EU permite modelo bivariado de forecast | Dashboard live con NA & EU sell-through → auto-ajuste de stock; ML que dispare campañas si curva difiere >2σ | Precisión forecast 4 semanas / % stock-outs evitados |
| 8 | **UX como ventaja competitiva** | El valle 2010–15 muestra fuga a digital | Onboarding guiado + métricas UX (T-tutorial, clicks perdidos); pulse surveys in-game tras 30 min | CSAT in-game ≥4/5 / Reducción drop tutorial 20 % |
| 9 | **Comunidades creadas, no compradas** | Juegos que sobre-indexan en EU tienen fuerte presencia e-sports/streamers | Programa oficial de creadores: acceso anticipado + revenue share; API para mods y mapas | UGC horas vistas |
| 10 | **Ciclo hardware–software sincronizado** | Pico de ventas 18–24 meses post-lanzamiento de consola | Roadmap de IPs flagship alineado a año 1 de nueva generación; beta cerrada con telemetría mes −6 | Ventas 90 días vs objetivo / Net Promoter Score beta |

---

## Valoración global del proyecto

### Fortalezas

**Solidez analítica.** El uso combinado de gráficos de barras, series de tiempo, scatter plots con R reportado y un heatmap de correlaciones demuestra manejo competente del toolset de análisis exploratorio de datos. El R=0.90 en el scatter EU vs. Global es un resultado estadístico concreto y verificable, no una intuición.

**Traducción datos → decisión.** La tabla de 10 palancas es el punto más fuerte del trabajo: cada insight tiene una acción operativa concreta y un KPI medible asociado. Esto es exactamente lo que se espera de un proyecto de Business Analytics —no solo describir, sino prescribir.

**Coherencia narrativa.** La presentación sigue una lógica limpia: contexto geográfico → géneros dominantes → evolución temporal → análisis por plataforma → correlaciones → recomendaciones. El flujo es natural y acumulativo.

**Diseño temático consistente.** Usar fondos de videojuegos retro (Street Fighter, Mortal Kombat, Mario Kart, etc.) como escenografía de cada slide no es solo estética —es comunicación. Ancla emocionalmente al audiencia en el objeto de estudio y hace la presentación memorable.

### Áreas de mejora

**Limitación temporal del dataset.** El análisis cubre ventas físicas hasta 2016. En 2026, el mercado es mayoritariamente digital, móvil y de servicios (Game Pass, PlayStation Plus, F2P con microtransacciones). Las 10 palancas son válidas, pero deberían explicitarse como "aplicables al canal físico/inicial" o actualizarse con datos más recientes para no perder vigencia.

**Causalidad vs. correlación.** El R=0.90 entre EU y ventas globales es impresionante, pero podría estar inflado por el propio peso de EU en la variable Global_Sales. Sería más robusto analizar la correlación de EU con (Global − EU) para confirmar poder predictivo real.

**Japón como mercado de nicho estratégico.** El análisis correcto identifica la baja correlación de JP, pero las recomendaciones de localización podrían profundizar más: ¿qué géneros específicos sobre-indexan en JP? ¿Cuáles son las IPs con mayor tracción? Una segmentación por género dentro de JP añadiría accionabilidad.

**Ausencia de benchmarks de competidores.** Las recomendaciones de KPI (ej. "CSAT in-game ≥4/5") se presentan como metas absolutas sin referencia a benchmarks de la industria. Conectar esos números a datos públicos de publishers líderes (Activision, Nintendo, EA) fortalecería la propuesta.

---

## Conclusión

El trabajo demuestra que los datos históricos de ventas de videojuegos, bien analizados, revelan patrones estructurales robustos: la hegemonía de NA+EU como termómetro global, el excentricismo estratégico de Japón, el declive irreversible del físico y la concentración de valor en pocos géneros de alto volumen. Las 10 palancas estratégicas propuestas son accionables, medibles y coherentes con la evidencia presentada. Es un proyecto sólido que combina rigor analítico con comunicación efectiva.
