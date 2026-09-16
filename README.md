# MH Tour V4.8 — AUTO ONLINE (LiveKit Cloud Test)

Versi ini mengubah MH Tour dari server lokal/hotspot menjadi **AUTO ONLINE** menggunakan LiveKit Cloud Development Token Server untuk pengujian.

## Yang berubah

- Tidak lagi memakai `192.168.43.1`.
- Tidak lagi membutuhkan server Node/Express lokal untuk pengujian.
- Guide dan Jemaah dapat memakai Wi-Fi atau data seluler masing-masing.
- Guide membuat kode rombongan langsung di HP.
- QR berisi kode rombongan dan room LiveKit.
- Jemaah cukup scan QR atau memasukkan kode `UM123456`.
- APK meminta access token dari LiveKit Cloud Development Token Server.
- API Secret LiveKit **tidak** dimasukkan ke APK.

## LiveKit Cloud

Project URL:
`wss://mh-tour-cmgw3l5g.livekit.cloud`

Development Token Server ID yang dikonfigurasi pada build uji:
`mhtour-19kg8e`

Token Server ID bukan API Secret. Namun Development Token Server hanya untuk development/testing dan tidak cocok untuk produksi karena frontend dapat meminta token dengan permissions yang luas. Untuk produksi, gunakan token endpoint/backend MH Tour sendiri.

## QR

Format QR:
`MHTOUR|JOIN|UM123456|mh-tour-UM123456`

Room name dibuat deterministik dari kode sehingga Guide dan Jemaah dapat menemukan room yang sama tanpa database sesi lokal.

## Produksi

Untuk versi produksi:
1. Pertahankan LiveKit Cloud sebagai media server.
2. Buat token endpoint HTTPS MH Tour.
3. Simpan `LIVEKIT_API_KEY` dan `LIVEKIT_API_SECRET` hanya di backend.
4. APK memakai `TokenSource.fromEndpoint(...)` atau mekanisme endpoint yang setara.
5. Jangan menaruh API Secret di APK/GitHub.

LiveKit mendokumentasikan Development Token Server sebagai workflow development/testing dan endpoint token sebagai workflow production.
