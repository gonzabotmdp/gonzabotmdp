# G. Arroyo

Administrador del cluster HPC de **IFIMAR-UNMDP** (Instituto de Investigaciones Físicas de Mar del Plata, CONICET).

Este perfil documenta contribuciones reales de IA asistida en tareas de administración de sistemas HPC: migraciones de stack de software, benchmarking, y fixes upstream a proyectos de código abierto usados por la comunidad científica.

## Contribuciones

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

## Enlaces institucionales

- [IFIMAR — Personal de apoyo](https://ifimar.conicet.gov.ar/personal-de-apoyo/)
- [IFIMAR — Servicios informáticos](https://ifimar.conicet.gov.ar/servicios-informaticos-para-la-comunidad-local/) ([EN](https://ifimar.conicet.gov.ar/it-services-for-the-local-community/))
- [Nota institucional, CCT Mar del Plata CONICET](https://mardelplata-conicet.gob.ar/30-03-2020-gonzalo-arroyo/)
- [ResearchGate](https://www.researchgate.net/profile/Gonzalo-Arroyo)
- [LinkedIn](https://ar.linkedin.com/in/alfamdq)
