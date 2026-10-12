# Ghosflow M3U Player — DASH update

## Apa yang berubah
- Mengekalkan UI dan ciri asal: import URL M3U/M3U8, kategori, carian, favorites, recently played, EPG XMLTV, fullscreen, dan PWA.
- Menambah enjin Shaka Player untuk MPEG-DASH `.mpd` yang disokong, sambil mengekalkan hls.js untuk HLS.
- Memperbaharui cache service worker supaya browser mendapatkan versi baharu.

## Deploy
1. Extract ZIP.
2. Upload/gantikan `index.html`, `manifest.webmanifest`, `sw.js`, dan `README.md` di root GitHub Pages repository.
3. Commit changes dan tunggu GitHub Pages deploy.
4. Di browser, lakukan hard refresh (`Ctrl+F5`). Jika app pernah dipasang, tutup/buka semula app selepas service worker dikemas kini.

## Nota playback
- Shaka Player dimuatkan daripada CDN jsDelivr (`shaka-player@5.2.12`). Sambungan internet diperlukan untuk mengambil library ini.
- DASH biasa/clear boleh dimainkan jika manifest, segmen, codec dan CORS dibenarkan oleh penyedia.
- Fail ini tidak memasukkan atau mengkonfigurasi kunci ClearKey, tidak mengabaikan DRM, dan tidak memintas sekatan penyedia. Kandungan yang disulitkan memerlukan hak akses serta kaedah DRM/lesen yang dibenarkan oleh penyedia.
- Mengaktifkan Shaka tidak boleh mengatasi CORS, token tamat tempoh, had peranti atau sekatan rangkaian penyedia.
- URL playlist dan kandungan yang dihantar ke browser boleh diperiksa oleh pengguna yang mengaksesnya; jangan simpan rahsia atau kunci dalam kod frontend awam.

## Sumber
- Shaka Player documentation: https://shaka-player.github.io/shaka-player/docs/api/tutorial-basic-usage.html
- Shaka Player releases: https://github.com/shaka-project/shaka-player/releases


## Kemas kini versi DASH / cache
- Versi ini menaikkan cache Service Worker kepada `ghosflow-player-v2` supaya browser menggantikan fail HTML lama yang mungkin masih tersimpan.
- Selepas upload semua fail ke root repository dan commit, buka laman semula. Jika masih versi lama, Chrome DevTools > Application > Service Workers > Unregister, kemudian Storage > Clear site data, dan reload laman.
- Sokongan DASH tidak automatik membuka kandungan yang dilindungi DRM; ia memerlukan konfigurasi lesen/kunci yang dibenarkan oleh penyedia.
