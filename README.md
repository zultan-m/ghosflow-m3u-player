# Ghosflow M3U Player

Aplikasi web ringan untuk memuat URL playlist M3U/M3U8, memainkan stream, kategori, carian, favorites, recent channels, fullscreen dan EPG XMLTV.

## Cara guna
1. Extract folder ini.
2. Host kandungan folder pada hosting HTTPS yang menyokong static files (contohnya GitHub Pages, Cloudflare Pages atau hosting sendiri).
3. Buka URL laman, tampal URL playlist `.m3u` / `.m3u8`, tekan **Load playlist**.
4. Untuk EPG, masukkan URL XMLTV `.xml` dan tekan **Load EPG**.
5. Pada Android, buka URL HTTPS dalam Chrome dan pilih menu **Install app** / **Add to Home screen**.

## Penting
- Disebabkan sekatan browser (CORS), URL playlist dan XMLTV perlu membenarkan fetch dari origin laman ini. Jika tidak, gunakan sumber yang menyokong CORS atau backend/proxy yang anda kawal dan dibenarkan oleh penyedia.
- HLS menggunakan hls.js daripada CDN; Safari/iOS boleh memainkan HLS native jika URL `.m3u8` disokong. Format lain bergantung pada browser/codec.
- EPG menggunakan XMLTV. Untuk padanan terbaik, playlist perlu mempunyai atribut `tvg-id` yang sepadan dengan ID channel dalam XMLTV.
- Favorites dan recent channels disimpan secara setempat pada browser melalui localStorage. URL playlist tidak disimpan secara automatik.
- PWA perlu dihidangkan melalui HTTPS (atau localhost) untuk pemasangan dan service worker.
- Untuk membungkus sebagai APK Android sebenar, gunakan Capacitor atau WebView wrapper selepas deploy. Projek ini sendiri ialah web/PWA, bukan fail APK siap pasang.
- Gunakan hanya playlist dan stream yang anda berhak akses.
