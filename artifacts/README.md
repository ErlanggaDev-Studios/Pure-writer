# Artefak Tinta 1.0.0 — Android native

Dibuat dari commit `a71f99b` (`feat(android): add native Kotlin Compose writing app`).

## 1. `tinta-android-1.0.0-debug.apk`

APK Android native (Kotlin + Jetpack Compose), siap dipasang sebagai **debug build**.

- Package: `id.tinta.app` · versi `1.0.0` (versionCode 1)
- minSdk 26 (Android 8.0) · target/compile SDK 35
- Label: **Tinta** · activity: `id.tinta.app.MainActivity`
- Ukuran ±17 MB · ditandatangani debug certificate `CN=Android Debug`
- Tidak meminta izin jaringan; tidak ada WebView, akun, iklan, analytics, atau paywall.

Pasang:

```bash
adb install -r tinta-android-1.0.0-debug.apk
```

Atau salin ke ponsel, buka, dan izinkan "Instal aplikasi tak dikenal" untuk aplikasi berkas
yang kamu pakai. Karena ini debug build, jangan pakai untuk distribusi publik; buat keystore
rilis sendiri.

SHA-256:

```
058d24d413c7c58a1910b0c5ca20efc3af3e9b850612dc80a64d5af79337715a
```

## 2. `tinta-1.0.0-source.zip`

Arsip sumber dari commit yang sama: proyek Android lengkap (`android/`), prototipe web
(`src/`), Gradle wrapper, README, dan dokumen `replica/` termasuk tangkapan layar web.

```bash
unzip tinta-1.0.0-source.zip -d tinta
cd tinta/android
./gradlew :app:assembleDebug
```

SHA-256:

```
965851d8b109faae6a5feb77f83dce20abf6d49e9ff14ffafee6344b551ab2d7
```

## 3. `tinta-1.0.0.html` — prototipe web (opsional)

Build web satu berkas dari commit sebelumnya, disimpan sebagai prototipe. Bukan artefak
utama. Bisa dibuka langsung di peramban; data tersimpan di `localStorage`. SHA-256:

```
cf05f91ee93c3694adb56dec4929b5939d579e235a44acc56b3dc3385b4f441b
```

## Verifikasi yang benar-benar dijalankan

- `./gradlew :app:assembleDebug` → BUILD SUCCESSFUL.
- `./gradlew :app:lintDebug` → BUILD SUCCESSFUL, **0 error**.
- `aapt dump badging` → package, versi, SDK, label, dan launchable activity sesuai.
- `apksigner verify --print-certs` → sertifikat debug valid.
- APK berisi `classes.dex`, `AndroidManifest.xml`, dan `resources.arsc`.

**Belum dijalankan di emulator atau perangkat.** Lingkungan build tidak memberi akses
`/dev/kvm`, jadi tidak ada uji buka aplikasi, alur UI, rotasi, process death, ekspor/impor,
atau pembaca layar. Kompilasi dan lint bukan bukti aplikasi berjalan mulus. Lakukan smoke
test perangkat sebelum menganggapnya siap rilis.

Batas lainnya: belum ada PDF/gambar/HTML/DOCX/EPUB, TTS, sinkronisasi cloud, undo/redo
khusus, atau drag-reorder bab. JSON lokal tidak dienkripsi dan tidak ada kunci aplikasi.
