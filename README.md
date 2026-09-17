# RHO_LAW — La ley de ρ como principio trans-dominio

**Tesis:** la ley ρ (colapso del observador cuando n_codevectors ≈ dimensión)
no es un fenómeno de VSA. Es un miembro de una FAMILIA de singularidades
por "saturación del observador" que aparece en dominios distintos.

## Estructura

- `domains/` — una carpeta por dominio con su manifestación de la ley
- `experiments/` — código corriendo cada manifestación
- `docs/` — análisis y referencias cruzadas

## Manifiestos de la ley ρ (tentativa)

| Dominio | Observable | "ρ" análogo | Colapso del observador |
|---|---|---|---|
| **VSA/HRR** | accuracy de decoding | n_vectors/dim | gram/pinv en ρ=1 |
| **Turbulencia (SDDF)** | curvatura espectral G[u] | Re/Re_corte | singularidad log |
| **Paloma-π bioacústica** | accuracy de clasificación | n_roles/N_HRR | idem FHRR |
| **MLP aprendido** | loss final | capacidad_ejemplos/N | sobreajuste |
| **Transformers** | accuracy atención | n_heads×dim/dim_embed | colapso de atención |

**La pregunta unificadora**: ¿en qué punto el observador deja de "ver" la
señal porque el sistema superó su capacidad de resolución? Ese punto es
una ley de escala distintiva del sistema.

## Conexión directa con SDDF (Navier-Stokes)

El observable G[u] = ∫(d ln E / d ln k)² d ln k tiene un comportamiento
logarítmico en Re INDEPENDIENTE del cutoff. Pero cuando cortás el espectro
por grilla (discretización), el error NO decae monótonamente — oscila. Es
el mismo patrón: el observador (grilla discreta) tiene un límite de
resolución, y la medición se "rompe" de forma no-monótona cerca del límite.

→ El patrón de la ley ρ está presente incluso en espectros de turbulencia.
