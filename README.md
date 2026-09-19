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

**El hallazgo clave de Collatz** (`experiments/exp_collatz_theorema.py`):
el azar puro con la misma estructura (P=1/3 + racimos geométricos) **acumula**
desviación (b≈0); Collatz **cancela** (b=−0.35). La equidistribución no es
pasiva — es un **atractor del sustrato**. El teorema a buscar:
*"|f_P − 1/3| decae como n^(−0.35) por órbita"* — si es asintótico, la
divergencia es imposible y la conjetura cae como corolario.

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
