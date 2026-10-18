```text
╭──────────────────────────────────────────────────────────────╮
│   r u s t - r e a d y - s m o k e                             │
│   [INFRA] template Rust siap CI · sejak 15 Sep 2026           │
╰──────────────────────────────────────────────────────────────╯
```

> Template Rust minimal — **1.98.1**, edition 2024, tanpa dependency aplikasi
> tambahan. Dipakai untuk memulai proyek baru atau memeriksa bahwa toolchain
> lokal sehat.

## Pakai

```bash
cargo run --locked          # menjalankan binary
rust-workbench check        # pemeriksaan standar (bila tool tersedia)
rust-workbench coverage     # laporan cakupan test
```

Pipeline manual — persis yang dijalankan CI:

```bash
cargo fmt --all -- --check
cargo clippy --locked --workspace --all-targets --all-features -- -D warnings
cargo test --locked --workspace --all-features
cargo doc --locked --workspace --all-features --no-deps
cargo build --locked --workspace --release
cargo audit
```

## Isi

| Path | Keterangan |
|---|---|
| `src/main.rs` | binary minimum |
| `.github/workflows/ci.yml` | CI Linux: fmt, clippy, test, doc, build |
| `.vscode/` | konfigurasi debug (`F5`) |
| `rust-toolchain.toml` | toolchain terpin (1.98.1) |
| `Cargo.lock` | ikut disimpan, sesuai kebiasaan proyek |

## Catatan

- Template belum punya test aplikasi; tambahkan test saat perilakunya sudah
  ditentukan.
- `cargo audit` memeriksa advisory RustSec yang diketahui — bukan jaminan
  bebas celah.
- Workflow CI baru bisa diverifikasi setelah repo ini dipublikasikan.

## Lisensi

MIT — lihat [LICENSE](LICENSE).
