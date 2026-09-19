# RHO_LAW — La ley de ρ como principio trans-dominio

**Tesis:** la ley ρ (colapso del observador cuando n_codevectors ≈ dimensión)
no es un fenómeno de VSA. Es un miembro de una FAMILIA de singularidades
por "saturación del observador" que aparece en dominios distintos.

**Formalización completa:** `docs/ESTRUCTURA_TRES_CAPAS.md` — la estructura de
tres capas (sustrato / observador / instrumento), los teoremas de la capa 1
por dominio, el hueco ensemble→órbita, los mecanismos de auto-regulación, y
el punto irreducible.

## Estructura

- `domains/` — una carpeta por dominio con su manifestación de la ley
- `experiments/` — código corriendo cada manifestación
- `docs/` — análisis y referencias cruzadas

## Los dominios verificados (con datos)

| Dominio | Parámetro admisible | Umbral exacto | Tipo de transición | Estado |
|---|---|---|---|---|
| **VSA/HRR** | ρ = n_cv/dim | **κ* = 5.81×10³** (banda [10³,10⁴]) | **puntual** (ancho cero) | ✅ 3 repos de datos |
| **HRR real** | ρ | idem (anti-resonancia) | puntual | ✅ |
| **BSC binario** | ρ | idem (gram 0.28 vs pure 1.0) | puntual | ✅ |
| **LiDAR** | clusters/voxel | ρ>1 colapsa (gram 1.0→0.33) | puntual | ✅ |
| **SDDF (turbulencia)** | κ del corte | banda ~10³-10⁴ | **no-monótona** (oscilante) | ✅ multi-observador |
| **Collatz** | f_P = visitas_P/N | **f_P* = 0.7075** (log₄(8/3), cond. LEH) | **gradual** (rampa) | ✅ 161 órbitas + forzado |

## El mecanismo de auto-regulación (la capa 1 protege)

Cada dominio tiene un mecanismo que mantiene el sistema estable — y es medible:

| Dominio | Mecanismo | Medido como |
|---|---|---|
| Collatz | **equidistribución-atractor** (auto-corrección activa) | \|f_P−0.5\| ~ n^(−0.35) vs null n^(−0.004) — 100k órbitas |
| Turbulencia | Tercer Motor (G[u] auto-regula) | G* plateau en DNS 2D |
| VSA | resonator puro (cleanup iterativo) | accuracy 1.0 en todo el grid |
| NS (audit CAOS) | localización de capas | error λ_q⁻¹ |

**El hallazgo clave de Collatz** (`experiments/exp_collatz_theorema.py`,
100k órbitas con null model correcto):

- **El null correcto** (P=1/3 + racimos geométricos, la misma estructura del
  mapa) **SÍ cancela** la desviación como predice CLT: b = −0.472 ≈ −0.5.
- **Collatz cancela MÁS LENTO**: b = −0.264 (vs medida invariante 0.324).
- **GAP +0.21: Collatz acumula MÁS desviación que el azar equivalente** —
  hay sustrato real en la desviación, no solo azar.
- **La cola existe**: 135/100.000 órbitas (0.135%) con |f_P−1/3|>0.15 —
  y TODAS convergen (ninguna divergencia real hasta n=2M).

**El teorema a buscar (formulación corregida):** la acumulación sobre el
azar es sustrato real; lo que falta es la **ACOTACIÓN**:

> *|f_P − 1/3| ≤ C para toda órbita, con C < f_P* − 1/3 = 0.374*

Esa acotación (si es cierta) + el umbral condicional = **la conjetura cae
como corolario**. Es un enunciado de teoría ergódica estándar (acotación de
la desviación de la medida invariante), más débil que LEH y más atacable.

## La tesis filosófica

Tres capas: **sustrato irreducible** (drift −2, balance 25/12, superposición)
→ **observador** (f_P, decoders, G[u]) → **instrumento** (grilla, κ, forzado).

El colapso vive en las capas 2-3. La capa 1 es invariante. Como la longitud
de onda es al color, **el balance del presupuesto dual es al colapso**:
existe sin observador, y todo lo demás se construye encima.

Un resultado negativo ("la señal no contiene esa información") puede ser un
artefacto de las capas 2-3. Antes de publicarlo, hay que probar al menos dos
clases de observadores.

## Experimentos cruzados

- `exp_ns_multi_observer.py` — 20 espectros SDDF × 5 observadores: los ratios
  entre ventanas son invariantes (CV≈0.24), G_total es artefacto (CV≈0.7)
- `exp_collatz_multi_observer.py` — 161 órbitas × 3 observadores: la
  convergencia es invariante (0 cruces, 0 drifts positivos)
- `exp_collatz_forzado.py` — el forzado de observador (ε≥0.10 cruza f_P* en
  la medición) NO genera divergencia real (termination 1.00 en todos los ε)
- `exp_null_model_periodograma.py` — el detector de Migdal es válido con
  null model calibrado (umbral amp≥0.02, p=0.007)

## Repos hermanos

- **Rylow999/fhrr-rho-collapse** — el paper técnico (ley ρ + κ*)
- **Rylow999/paloma-pi-v2** — la aplicación en bioacústica real
- **Rylow999/sddf** — Navier-Stokes (curvatura espectral)

*Per aspera, ad astra.*
