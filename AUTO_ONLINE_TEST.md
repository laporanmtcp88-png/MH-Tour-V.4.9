# MH Tour V4.8 AUTO ONLINE — Test Mode

## Status

This build is configured to use the LiveKit Cloud **Development Token Server** for testing.

- LiveKit project: `MH Tour`
- LiveKit WebSocket URL: `wss://mh-tour-cmgw3l5g.livekit.cloud`
- Development Token Server ID: `mhtour-19kg8e`

No LiveKit API secret is stored in the Android app.

## Test flow

1. Install the APK on a Guide phone and a Jemaah phone.
2. Give both phones normal internet access. They do not need to be on the same Wi-Fi.
3. Guide → **Mulai sebagai Guide**.
4. Enter Guide name.
5. Press **Buat Sesi Rombongan**.
6. A six-digit code and QR appear.
7. Jemaah → **Gabung sebagai Jemaah** → scan the QR, or type the six-digit code.
8. Guide → **Mulai Bicara**.
9. Jemaah should hear the Guide audio.

## Important

The Development Token Server is for development/testing only. It is intentionally not a production security boundary. Before public release, replace `TokenSource.fromDevelopmentTokenServer(...)` with a production token endpoint hosted by MH Tour. Keep `LIVEKIT_API_SECRET` only on that backend.
