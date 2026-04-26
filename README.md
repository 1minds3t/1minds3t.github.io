<!-- These images are generated and updated daily by a custom GitHub Action -->
<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/1minds3t/github_stats/master/generated/overview.svg#gh-dark-mode-only">
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/1minds3t/github_stats/master/generated/overview.svg#gh-light-mode-only">
    <img alt="1minds3t's GitHub Stats" src="https://raw.githubusercontent.com/1minds3t/github_stats/master/generated/overview.svg">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/1minds3t/github_stats/master/generated/languages.svg#gh-dark-mode-only">
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/1minds3t/github_stats/master/generated/languages.svg#gh-light-mode-only">
    <img alt="1minds3t's Language Stats" src="https://raw.githubusercontent.com/1minds3t/github_stats/master/generated/languages.svg">
  </picture>
</p>

<br>

<p align="center">
  <img src="https://raw.githubusercontent.com/1minds3t/omnipkg/main/.github/logo.svg" alt="omnipkg" width="72">
</p>

<h1 align="center">1minds3t</h1>

<p align="center">
  <code> Python · Rust · C · impossible is nothing.</code>
</p>

<p align="center">
  <a href="https://github.com/1minds3t/omnipkg"><img src="https://img.shields.io/badge/omnipkg-runtime_hypervisor-f97316?style=flat-square&labelColor=0d0d18&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdCb3g9IjAgMCAxNiAxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48Y2lyY2xlIGN4PSI4IiBjeT0iOCIgcj0iNyIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjZjk3MzE2IiBzdHJva2Utd2lkdGg9IjEuNSIvPjxsaW5lIHgxPSI4IiB5MT0iMSIgeDI9IjgiIHkyPSIxNSIgc3Ryb2tlPSIjZjk3MzE2IiBzdHJva2Utd2lkdGg9IjEuNSIvPjxsaW5lIHgxPSIxIiB5MT0iOCIgeDI9IjE1IiB5Mj0iOCIgc3Ryb2tlPSIjZjk3MzE2IiBzdHJva2Utd2lkdGg9IjEuNSIvPjwvc3ZnPg==" alt="omnipkg"></a>
  <a href="https://pypi.org/project/omnipkg/"><img src="https://img.shields.io/pypi/v/omnipkg?style=flat-square&labelColor=0d0d18&color=f97316&label=PyPI" alt="PyPI"></a>
  <a href="https://exotic-wheels.github.io/"><img src="https://img.shields.io/badge/exotic--wheels-PEP_503_index-22d3a0?style=flat-square&labelColor=0d0d18" alt="exotic-wheels"></a>
  <img src="https://img.shields.io/badge/started-May_2025-6b7280?style=flat-square&labelColor=0d0d18" alt="started">
</p>

---

```
$ 8pkg sync
  Python 3.8  ✅  52 active   Python 3.11 ✅  261 active · 33 bubbles
  Python 3.9  ✅  48 active   Python 3.12 ✅   41 active
  Python 3.10 ✅  44 active   Python 3.13 ✅   62 active
                              Python 3.14 ✅   56 active

  [SHA-CHECK] match=True  sha256:69545e99…
  ✅ Environment already matches lock file.
```

---

## what i'm building

Started May 2025. The goal from day one: make `pip install <anything>` work everywhere — fast, reproducible, CVE-aware — without fighting the existing ecosystem.

That turned into **omnipkg**: a Universal Python Runtime Hypervisor. Daemon worker pool, filesystem-isolated bubbles, multi-version Python concurrency in one env, zero-copy shared memory IPC between interpreter versions, dynamic CUDA loading, and a C dispatcher binary for <1ms startup.

Python is kept in RAM. The FFI layer is Rust. The critical paths are C. The policy engine is next.

> What others see as a decade-long problem, I see as a weekend project.

---

## the stack

```
┌──────────────────────────────────────────────────────┐
│              omnipkg  —  runtime hypervisor           │
│     daemon · bubbles · multi-version · zero-copy IPC  │
└────────────┬─────────────────────────────────────────┘
             │
   ┌─────────┼──────────┬───────────────────┐
   │         │          │                   │
uv-ffi   dispatcher.c  omnipatcher      exotic-wheels
Rust FFI  <1ms startup  CVE auto-patch   missing wheels
~2.78×uv               OSV · GHSA        PEP 503 index
   │
filelock-lts · urllib3-lts  (CVE LTS forks, py3.7–3.9)
```

---

## projects

| project | what | status |
|---|---|---|
| **[omnipkg](https://github.com/1minds3t/omnipkg)** | Universal Python Runtime Hypervisor — daemon, bubbles, multi-version, zero-copy IPC, CUDA | ✅ live on PyPI |
| **[uv-ffi](https://github.com/1minds3t/omnipkg)** | Rust FFI layer over uv, ~2.78× faster, 671+ wheels shipped | ✅ live |
| **[exotic-wheels](https://exotic-wheels.github.io/)** | PEP 503 wheel index for musllinux armv7l, aarch64, ppc64le — drop-in for pip | ✅ live |
| **omnipatcher** | CVE auto-patcher, OSV+GHSA scanner, diff transparency, reproducibility proofs | private |
| **[filelock-lts](https://github.com/1minds3t/filelock-lts)** | CVE-2025-68146 + CVE-2026-22701 patched for py3.7–3.9 | ✅ live |
| **[filelock-lts](https://github.com/1minds3t/urllib3-lts)** | 6 CVEs patched for py3.7–3.8 | ✅ live |

---

## roadmap

- [x] **Phase 1 — Foundation** · daemon · bubbles · uv-ffi · zero-copy IPC · dynamic CUDA · C dispatcher · LTS forks · exotic-wheels infra
- [x] **Phase 2 — CI Hardening** · musllinux armv7l builds · abi3 C extension · cffi + psutil wheels · GH Actions auto-index *(active)*
- [ ] **Phase 3 — CVE Policy Engine** · OSV+GHSA scanner · warn / block / sandbox / lts policy · import hook · reproducibility proofs
- [ ] **Phase 4 — exotic-wheels Growth** · all major packages × all exotic platforms · omnibuilder auto-upload · lockfile integration
- [ ] **Phase 5 — pip just works everywhere** · `8pkg install <anything>` on every platform · lock files travel frictionlessly

---

<p align="center">
  <a href="https://github.com/1minds3t/omnipkg">omnipkg</a> ·
  <a href="https://exotic-wheels.github.io/">exotic-wheels</a> ·
  <a href="https://pypi.org/project/omnipkg/">PyPI</a> ·
  <a href="https://github.com/exotic-wheels/exotic-wheels.github.io/issues/new">request a wheel</a> ·
  <a href="mailto:1minds3t@proton.me">1minds3t@proton.me</a>
</p>
