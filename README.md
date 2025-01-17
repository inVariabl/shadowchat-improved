# Shadowchat Improved
- Self-hosted, non-custodial and minimalist Monero (XMR) superchat system written in Go.
- Provides an admin view page to see donations with corresponding comments.
- Provides notification methods usable in OBS with an HTML page.

![Main Donation Page](media/index.png)

![Payment Page](media/pay.png)

![Superchat Message Page](media/view.png)

# Added Features
- XMR to USD conversion
- Word count
- Click-to-copy payment address
- Mark superchat messages as read
- UI improvements

---

To see a working instance of shadowchat, see [xmr.lukesmith.xyz](https://xmr.lukesmith.xyz).

# Installation
1. ```apt install golang```
2. ```git clone https://git.sr.ht/~anon_/shadowchat```
4. ```cd shadowchat```
2. ```go install github.com/skip2/go-qrcode@latest```
5. ```go mod init shadowchat && go mod tidy```
6. edit ```config.json```
7. ```go run main.go```

A webserver at 127.0.0.1:8900 is running. Pressing the pay button will result in a 500 Error if the `monero-wallet-rpc` is not running.
This is designed to be run on a cloud server with nginx proxypass for TLS.

# Monero Setup
1. Generate a view only wallet using the `monero-wallet-gui` from getmonero.org. Preferably with no password
2. Copy the newly generated `walletname_viewonly` and `walletname_viewonly.keys` files to your VPS
3. Download the `monero-wallet-rpc` binary that is bundled with the getmonero.org wallets.
4. Start the RPC wallet: `monero-wallet-rpc --rpc-bind-port 28088 --daemon-address https://xmr-node.cakewallet.com:18081 --wallet-file /opt/wallet/walletname_viewonly --disable-rpc-login --password ""`

# Usage
- Visit 127.0.0.1:8900/view to view your superchat history
- Visit 127.0.0.1:8900/alert?auth=adminadmin to see notifications
- The default username is `admin` and password `adminadmin`. Change these in `main.go`
- Edit web/index.html and web/style.css to customize your front page!

# OBS
- Add a Browser source in obs and point it to `https://example.com/alert?auth=adminadmin`

# Future plans
- Blocklist for naughty words
- Widget for OBS displaying top donators
- Settings page for on-the-fly changes (minimum donation amount, hide all amounts, etc.)

# License
GPLv3

### Origin
This comes from [https://git.sr.ht/~anon_/shadowchat](https://git.sr.ht/~anon_/shadowchat) and is not Luke's original work.
