# Changelog

<!-- next-header -->

## Unreleased

## v0.2.0 - 2026-08-04

### Android/macOS platform support
- **macOS Mach-O core dumps** via `--macho-core` (3e998e0)
- **Non-Windows minidumps** - Linux/Android-produced minidumps are now supported (b135636)

### Engine & build coverage
- **Editor build support** - `--editor` sets `UE_EDITOR`, `WITH_EDITOR`, `WITH_EDITORONLY_DATA` (b24afe0)
- **UE 5.8** struct layout fixes (a2816b3)
- **UE < 4.22** FName extraction fixed and implemented (07b0c13)
- **UE 4.20** `NumElementsPerChunk` is now derived rather than assumed (055cb46)
- **Case-preserving FNames** are auto-detected. Also fixes case-preserving handling on UE 5.1+ (5e2d4e1, e920313)
- **Cross-platform struct layout**: `--target` triple (e.g. `aarch64-linux-android`, defaults to `x86_64-pc-windows-msvc`) (5ca29f0, 895a43c)

### CLI
- Explicit arg based address/config overrides: `--fname-pool`, `--guobject-array`, `--engine-version`, `--image-base` (850f059)
- Outfile `-` now writes to stdout along with `--format {jmap,jmap-gz,usmap,header}` (db9e92d)
- `--skip-vtables` / `--skip-objects` (9012989)
- Reworked diagnostics: `-v`/`-vv` verbosity levels, `-q` quiet mode, warning counting and a summary line (de1d0b1, db9e92d)
- `--module NAME` resolves `--fname-pool`/`--guobject-array` as RVAs from a named module's load address (e.g. `libUnreal.so`), and defaults `--image-base` to that module (909bce9)
- New build config flags: `--pack-fuobject-item`, `--fuobject-flags-refcount`, `--stats`, `--case-preserving`, `--build-changelist` (cebbbbf, 850f059)

### Format & library
- `jmap`: added `UClass::interfaces` (aa357c6)
- `jmap`: `Address` now serializes as hex (665855b)
- `jmap_dumper`: memory access is now async, and memory traits no longer pollute generics throughout the API; memory writing is supported (55d3227, 6c7114c)
- `jmap_dumper`: general API cleanup, reworked generic memory-source initialization, exposed a field-owner API (52ee7ca, 0c31775, f3b1b41)

### Tooling
- `scripts/frida_minidump.py` + `scripts/mdwrite.py` - capture full-memory minidumps from a Frida-attached process (6d0f8ed)
