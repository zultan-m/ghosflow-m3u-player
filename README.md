# Ghosflow M3U Player — Playback Diagnostics

## Perubahan versi ini
- Kekalkan import playlist M3U, kategori, carian, favorites, recently played, EPG XMLTV, fullscreen dan PWA.
- Kekalkan hls.js untuk HLS dan Shaka Player untuk DASH.
- Baca metadata `#KODIPROP` yang berkaitan dengan manifest dan jenis DRM untuk menandakan channel; nilai `license_key` tidak disimpan dalam metadata parsed, dipaparkan, atau dimasukkan ke konfigurasi player.
- Paparkan label DASH/DRM serta diagnostik yang membezakan kemungkinan HTTP 403, CORS, rangkaian dan konfigurasi DRM yang diperlukan.
- Naikkan cache Service Worker kepada `ghosflow-player-v3-diagnostics`.

## Deploy ke GitHub Pages
1. Extract ZIP.
2. Upload/gantikan `index.html`, `manifest.webmanifest`, `sw.js`, dan `README.md` di root repository.
3. Commit changes dan tunggu GitHub Pages selesai deploy.
4. Buka semula laman dan tekan `Ctrl+F5`. Jika masih paparan lama, Chrome DevTools → Application → Service Workers → Unregister; kemudian Storage → Clear site data dan reload.

## Had playback
- Shaka Player dimuatkan daripada CDN jsDelivr (`shaka-player@5.2.12`); sambungan internet diperlukan.
- Pengesanan `#KODIPROP` hanya untuk diagnostik. Arahan Kodi bukan konfigurasi DRM automatik untuk browser.
- Kandungan DASH terlindung memerlukan konfigurasi DRM/lesen web yang sah serta kebenaran penyedia. Projek ini tidak memasukkan kunci DRM, tidak memintas DRM dan tidak mengatasi sekatan akses penyedia.
- Jika manifest/segmen/endpoint lesen memulangkan HTTP 403 atau tidak memberikan CORS yang diperlukan, player akan melaporkan kemungkinan puncanya; CORS pada Worker redirect tidak menggantikan kebenaran daripada pelayan akhir.
- URL playlist dan kandungan yang dihantar kepada browser boleh diperiksa pengguna yang mengaksesnya. Jangan letak token rahsia atau kunci DRM dalam frontend awam.

## Sumber teknikal
- Shaka Player: https://shaka-player.github.io/shaka-player/docs/api/tutorial-basic-usage.html
- Shaka Player error model: https://shaka-player-demo.appspot.com/docs/api/shaka.util.Error.html
