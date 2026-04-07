# ▣ ScreenLink

> **Serverless, zero-signup P2P screen sharing — one HTML file, no install required.**

ScreenLink lets you share your screen with anyone using only a browser. There is no server, no account, no extension, and no data ever leaves your machine to a third party. It runs entirely from a single `.html` file, including directly off `file://`.

---

## ✨ Features

- **100% serverless** — pure WebRTC peer-to-peer, no relay or backend
- **No signup, no tracking, no data stored**
- **Single file** — the entire app is one `.html` file you can save and run anywhere
- **Works from `file://`** — no web server needed, just open it in a browser
- **Audio + video** — shares your screen with optional system audio
- **Live preview** — the host sees a local preview while sharing
- **Fullscreen viewer** — viewer can go fullscreen with one click
- **30 fps capture** — smooth, high-quality stream

---

## 🚀 Usage

No installation required. Just open `screenlink.html` in a modern browser.

### Sharing your screen (Host)

1. Open `screenlink.html` and go to the **Share Screen** tab
2. Click **Start Sharing** and pick a window or your full screen
3. Click **Generate Offer** — a short text blob will appear
4. Copy the blob and send it to your viewer (chat, email, anything works)
5. Wait for the viewer to send back their **Answer** blob
6. Paste their Answer and click **Connect** — you're live ✓

### Viewing a screen (Viewer)

1. Open `screenlink.html` and go to the **View Screen** tab
2. Paste the host's **Offer** blob
3. Click **Generate Answer** — your own blob will appear
4. Copy it and send it back to the host
5. The live stream appears automatically once the host connects ✓

---

## 🔧 How It Works

ScreenLink uses **WebRTC** with **manual SDP signaling** — the standard WebRTC handshake, but without a signaling server. Instead, you act as the signaling channel by copy-pasting two short base64 blobs between the host and viewer.

```
Host                              Viewer
 │                                  │
 │── Offer blob ──────────────────► │
 │                                  │ (generates Answer)
 │◄─────────────────── Answer blob ─│
 │                                  │
 └──────── P2P stream established ──┘
```

ICE candidates are gathered using Google's public STUN servers (`stun.l.google.com`). Once the connection is established, all media flows **directly between the two browsers** — no data touches any server.

---

## 🌐 Browser Compatibility

| Browser | Supported |
|---|---|
| Chrome / Chromium | ✅ |
| Edge | ✅ |
| Firefox | ✅ |
| Safari 15.4+ | ✅ |

> **Note:** `getDisplayMedia` (screen capture) requires a secure context (`https://` or `file://`). It will not work on plain `http://`.

---

## ⚠️ Limitations

- Requires **both parties to be online at the same time** to exchange blobs
- May not work if one or both peers are behind a strict corporate firewall/NAT that blocks WebRTC (no TURN server is included)
- Screen capture permission must be granted by the host's browser

---

## 📁 Project Structure

```
webshare/
└── screenlink.html   # The entire app — HTML, CSS, and JS in one file
```

---

## 📄 License

MIT — do whatever you want with it.
