# G. Arroyo

**🇬🇧 English** · [🇦🇷 Español](#español)

HPC cluster administrator at **IFIMAR-UNMDP** (Institute of Physics Research of Mar del Plata, CONICET), Argentina.

This profile documents real contributions of AI-assisted work in HPC system administration: software stack migrations, benchmarking, and upstream fixes to open-source projects used by the scientific community.

## 🤖 Project: [gonzabot](https://github.com/gonzabotmdp/gonzabot)

An AI assistant for HPC users (Slurm + Spack) that checks an `sbatch` **before** it runs and fixes configuration mistakes, resource misuse and oversized resource requests, combining deterministic rules with a local LLM (served with [vLLM](https://github.com/vllm-project/vllm)), so no data leaves the cluster.

In production since 2026 on the IFIMAR cluster. Measured real cases: up to **2.7x** faster after applying its suggestion (same node, before/after). No external Python dependencies beyond the standard library. Designed to be gentle on the scheduler: see [Load on Slurm](https://github.com/gonzabotmdp/gonzabot#load-on-slurm-and-on-the-login-node).

**→ [Repository](https://github.com/gonzabotmdp/gonzabot) · [README in English](https://github.com/gonzabotmdp/gonzabot/blob/main/README.md) · [README en español](https://github.com/gonzabotmdp/gonzabot/blob/main/README.es.md)**

## Contributions

- [potfit/potfit#121](https://github.com/potfit/potfit/pull/121): compatibility fix for modern LAPACK/LAPACKE headers (`LAPACK_FORTRAN_STRLEN_END` convention), found while packaging potfit for Spack against OpenBLAS (no Intel/MKL) on AMD Zen4. **Merged** (adapted by the maintainer in potfit/potfit#122).
- [openxla/xla#47794](https://github.com/openxla/xla/pull/47794): fix for a duplicate include of `cupti_driver_cbid.h` (enum redefinition) when building TensorFlow with `HERMETIC_CUDA_VERSION=12.4.1`, to run on GPUs whose driver does not support CUDA 12.5+. Redirected from tensorflow/tensorflow#125963 (the file is vendored from openxla/xla). **Approved**, awaiting merge.
- Twelve fixes to recipes in [spack/spack-packages](https://github.com/spack/spack-packages), found while packaging the full HPC stack with AOCC + AMD Zen4:
  - [#6202](https://github.com/spack/spack-packages/pull/6202) octave: boolean logic bug + missing GL/GLU dependencies for `+qt`. **Approved**.
  - [#6203](https://github.com/spack/spack-packages/pull/6203) hpl: nvblas false positive in the BLAS auto-probe.
  - [#6204](https://github.com/spack/spack-packages/pull/6204) scafacos: malformed `.pc` file (root cause in `configure.ac`, with our own upstream fix in scafacos/scafacos#44).
  - [#6205](https://github.com/spack/spack-packages/pull/6205) gnuplot: build broken with `ld.lld` (clang/AOCC).
  - [#6206](https://github.com/spack/spack-packages/pull/6206) grace: Motif detection broken on builds with embedded Xpm + GCC 14+ strictness. **Approved**.
  - [#6207](https://github.com/spack/spack-packages/pull/6207) lammps: `CUDA_HOST_COMPILER` (a legacy FindCUDA variable) was never set, so the chosen CUDA host compiler was ignored. **Merged**.
  - [#6269](https://github.com/spack/spack-packages/pull/6269) spades: missing `<cstdint>` under GCC 14 (111 files affected, solved by forcing the include at compiler level).
  - [#6270](https://github.com/spack/spack-packages/pull/6270) metaeuk: same `<cstdint>` bug under GCC 14 in the vendored mmseqs2 (47 files affected).
  - [#6271](https://github.com/spack/spack-packages/pull/6271) boost: bjam bootstrap broken under GCC 14 in `@1.56.0` (undeclared `file_query`, a real missing include).
  - [#6272](https://github.com/spack/spack-packages/pull/6272) sepp: build broken on Python 3.12+ because `distutils` was removed (obsolete 2010 bootstrap).
  - [#6273](https://github.com/spack/spack-packages/pull/6273) py-quast: vestigial pin to boost@1.56.0 removed, Python 3.12+ compatibility, and permissions of a binary (`minimap2`) that was compiled on first use instead of at install time.
  - [#6274](https://github.com/spack/spack-packages/pull/6274) augustus: `TABIX` path never patched in `bam2wig`, which broke under Spack.

## Institutional links

- [IFIMAR: support staff](https://ifimar.conicet.gov.ar/personal-de-apoyo/) (in Spanish)
- [IFIMAR: IT services](https://ifimar.conicet.gov.ar/it-services-for-the-local-community/) ([ES](https://ifimar.conicet.gov.ar/servicios-informaticos-para-la-comunidad-local/))
- [Institutional note, CCT Mar del Plata CONICET](https://mardelplata-conicet.gob.ar/30-03-2020-gonzalo-arroyo/) (in Spanish)
- [ResearchGate](https://www.researchgate.net/profile/Gonzalo-Arroyo)
- [LinkedIn](https://ar.linkedin.com/in/alfamdq)

---

## Español

Administrador del cluster HPC de **IFIMAR-UNMDP** (Instituto de Investigaciones Físicas de Mar del Plata, CONICET).

Este perfil documenta contribuciones reales de IA asistida en tareas de administración de sistemas HPC: migraciones de stack de software, benchmarking, y fixes upstream a proyectos de código abierto usados por la comunidad científica.

### 🤖 Proyecto: [gonzabot](https://github.com/gonzabotmdp/gonzabot)

Asistente de IA para usuarios de HPC (Slurm + Spack) que revisa un `sbatch` **antes** de correrlo y corrige errores de configuración, mal uso de recursos, y pedidos de recursos sobredimensionados — combinando reglas determinísticas con un LLM local (vía [vLLM](https://github.com/vllm-project/vllm)).

En producción desde 2026 en el cluster de IFIMAR. Casos reales medidos: hasta **2.7x** más rápido tras aplicar su sugerencia (mismo nodo, antes/después). Sin dependencias externas de Python más allá de la librería estándar.

**→ [Repositorio](https://github.com/gonzabotmdp/gonzabot) · [README en español](https://github.com/gonzabotmdp/gonzabot/blob/main/README.es.md)**

### Contribuciones

- [potfit/potfit#121](https://github.com/potfit/potfit/pull/121) — fix de compatibilidad con headers LAPACK/LAPACKE modernos (convención `LAPACK_FORTRAN_STRLEN_END`), encontrado al empaquetar potfit para Spack contra OpenBLAS (sin Intel/MKL) en AMD Zen4. **Mergeado** (adaptado por el maintainer en potfit/potfit#122).
- [openxla/xla#47794](https://github.com/openxla/xla/pull/47794) — fix de inclusión duplicada de `cupti_driver_cbid.h` (redefinición de enum) al compilar TensorFlow con `HERMETIC_CUDA_VERSION=12.4.1`, para correr en GPUs con driver que no soporta CUDA 12.5+. Redirigido desde tensorflow/tensorflow#125963 (el archivo es vendored desde openxla/xla). **Aprobado**, esperando merge.
- Doce fixes a recipes de [spack/spack-packages](https://github.com/spack/spack-packages), encontrados empaquetando el stack HPC completo con AOCC + AMD Zen4:
  - [#6202](https://github.com/spack/spack-packages/pull/6202) octave — bug de lógica booleana + deps GL/GLU faltantes para `+qt`. **Aprobado**.
  - [#6203](https://github.com/spack/spack-packages/pull/6203) hpl — falso positivo de nvblas en el auto-probe de BLAS.
  - [#6204](https://github.com/spack/spack-packages/pull/6204) scafacos — `.pc` mal formado (causa raíz en `configure.ac`, con fix upstream propio en scafacos/scafacos#44).
  - [#6205](https://github.com/spack/spack-packages/pull/6205) gnuplot — build roto con `ld.lld` (clang/AOCC).
  - [#6206](https://github.com/spack/spack-packages/pull/6206) grace — detección de Motif rota en builds con Xpm embebido + strictness de GCC14+. **Aprobado**.
  - [#6207](https://github.com/spack/spack-packages/pull/6207) lammps — `CUDA_HOST_COMPILER` (variable legacy de FindCUDA) nunca se seteaba, ignorando el compilador host de CUDA elegido. **Mergeado**.
  - [#6269](https://github.com/spack/spack-packages/pull/6269) spades — `<cstdint>` faltante bajo GCC 14 (111 archivos afectados, resuelto forzando el include a nivel de compilador).
  - [#6270](https://github.com/spack/spack-packages/pull/6270) metaeuk — mismo bug de `<cstdint>` bajo GCC 14 en el mmseqs2 vendorizado (47 archivos afectados).
  - [#6271](https://github.com/spack/spack-packages/pull/6271) boost — bootstrap de bjam roto bajo GCC 14 en `@1.56.0` (`file_query` sin declarar, include faltante real).
  - [#6272](https://github.com/spack/spack-packages/pull/6272) sepp — build roto en Python 3.12+ por remoción de `distutils` (bootstrap obsoleto de 2010).
  - [#6273](https://github.com/spack/spack-packages/pull/6273) py-quast — pin vestigial a boost@1.56.0 eliminado, compat Python 3.12+, y permisos de un binario (`minimap2`) que se compilaba en el primer uso en vez de en el install.
  - [#6274](https://github.com/spack/spack-packages/pull/6274) augustus — path de `TABIX` nunca parcheado en `bam2wig`, rompía bajo Spack.

### Enlaces institucionales

- [IFIMAR — Personal de apoyo](https://ifimar.conicet.gov.ar/personal-de-apoyo/)
- [IFIMAR — Servicios informáticos](https://ifimar.conicet.gov.ar/servicios-informaticos-para-la-comunidad-local/) ([EN](https://ifimar.conicet.gov.ar/it-services-for-the-local-community/))
- [Nota institucional, CCT Mar del Plata CONICET](https://mardelplata-conicet.gob.ar/30-03-2020-gonzalo-arroyo/)
- [ResearchGate](https://www.researchgate.net/profile/Gonzalo-Arroyo)
- [LinkedIn](https://ar.linkedin.com/in/alfamdq)
