# Whitelisted NFT minting on Webflow

![Mint widget](public/images/screenshot.png)

Check out our ready-to-use minting website template: https://textapes.art

[Contact us](https://buildship.dev) to get this Webflow template & create your Opensea-independent NFT collection

## How to use?
1. Open Webflow website editor
2. Create a new [Embedded HTML code](https://university.webflow.com/lesson/custom-code-embed) block (at least **Basic** site plan required)
3. Copy & paste this code in Webflow Embed block
```html
<script>
   CONTRACT_ADDRESS = "<your contract address here>"
   NETWORK_ID = 1
   // insert Buildship whitelist ID to enable "Join whitelist"
   JOIN_WHITELIST_ID = undefined
   // for public mint
   MAX_PER_MINT = 20
</script>
<script src="https://nftcomponents-git-feature-whitelist-buildship.vercel.app/static/js/main.js"></script>
<link href="https://nftcomponents-git-feature-whitelist-buildship.vercel.app/static/css/main.css" rel="stylesheet">
```
4. If you have your Ethereum NFT contract, insert your contract address in `CONTRACT_ADDRESS` field. If you don't, [contact us](https://buildship.dev).
5. Create a button with ID `mint-button` to your Webflow site.
6. You're done 🎉


### Example for testing
```html
TODO
```

## Analytics

How can you add analytics to your minting website? Currently, we support tracking these events:

```
connect-wallet-success

whitelist-mint-button-click
whitelist-mint-success
whitelist-mint-reject
whitelist-mint-error

public-sale-mint-button-click
public-sale-mint-success
public-sale-mint-reject
public-sale-mint-error
```

To track ones you're interested in, append this code block to your Webflow Embed block AFTER your buildship script:

```html
<script>
    // example tracking event with data
    analytics.addEventListener('connect-wallet-success', (data) => console.log('connect-wallet-success', data));

    // track event into your Yandex Metrika
    analytics.addEventListener('connect-wallet-success', () => ym(99999, 'reachGoal', 'WalletConnected'));

    // track event into your Google Analytics
    analytics.addEventListener('connect-wallet-success', () => ga('send', 'event', 'WalletConnected'));

    // track event into your Facebook Pixel
    analytics.addEventListener('connect-wallet-success', () => fbq('track', 'WalletConnected'));

    // track many events at once:
    analytics.addEventListener('public-sale-mint-success', () => ym(99999, 'reachGoal', 'MintSuccess'));
    analytics.addEventListener('public-sale-mint-error', () => ym(99999, 'reachGoal', 'MintError'));
    analytics.addEventListener('public-sale-mint-reject', () => ym(99999, 'reachGoal', 'MintReject'));
</script>
```

Full example:

```html
<script>
   CONTRACT_ADDRESS = "<your contract address here>"
   NETWORK_ID = 1
   // insert Buildship whitelist ID to enable "Join whitelist"
   JOIN_WHITELIST_ID = undefined
   // for public mint
   MAX_PER_MINT = 20
</script>
<script src="https://nftcomponents-git-feature-whitelist-buildship.vercel.app/static/js/main.js"></script>
<link href="https://nftcomponents-git-feature-whitelist-buildship.vercel.app/static/css/main.css" rel="stylesheet">

<script>
    analytics.addEventListener('public-sale-mint-success', () => ym(99999, 'reachGoal', 'MintSuccess'));
    analytics.addEventListener('public-sale-mint-error', () => ym(99999, 'reachGoal', 'MintError'));
    analytics.addEventListener('public-sale-mint-reject', () => ym(99999, 'reachGoal', 'MintReject'));
</script>
```

If this doesn't work, first check the console for errors, and see if it outputs "ANALYTICS" when events are happening.

## FAQ

### I'm confused / it's not working, can you help me?
Yes, absolutely! You can contact us at https://buildship.dev, or open a [GitHub issue](https://github.com/buildship-dev/webflow-nft-components/issues/new)

### How to add "Connect wallet" button?
Mint button will ask to connect wallet, so it's not necessary to add a "Connect wallet" button.

If you still want to do it, create a Webflow button with ID `connect`.

### How to add minted counter?
Just create two text elements and assign them:
- `minted-counter` ID to display minted number
- `total-counter` ID to display collection max size

### How to use this with Polygon, Binance, or other Ethereum-based networks?
It's easy! Change `NETWORK_ID` in the code snippet:

- Ethereum Rinkeby Testnet: `NETWORK_ID = 4`
- Polygon `NETWORK_ID = 137`
- Binance `NETWORK_ID = 56`
- For others visit: https://chainlist.org/
5. Change `NETWORK_ID` if you're using something other than Ethereum:
    - Ethereum Rinkeby Testnet: `NETWORK_ID = 4`
    - Polygon `NETWORK_ID = 137`
    - Binance `NETWORK_ID = 56`
6. Create a button with ID `mint-button` to your Webflow site.
7. You're done 🎉

Minting will work via Metamask wallet, and will ask to connect the wallet first, so it's not necessary to add a "Connect wallet" button.

If you don't know how to code or want to launch fast, get Webflow NFT minting templates at https://buildship.dev
