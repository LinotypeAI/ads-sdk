# Linotype Ads SDK

Official Linotype Ads SDK for integrating contextual ads into web applications and AI assistants.
Also available as a Node.js package.

## Installation

For Chrome Extensions:
```bash
git clone https://github.com/LinotypeAI/ads-sdk.git
```

## For Chrome Extensions

### Quick Start

In your extension's HTML file (e.g., `popup.html`) add:
```html
<script src="ads-sdk/ads-sdk.js"></script>
```

### Instantiate

In your extension's JS file (e.g., `popup.js`) add:
```javascript
const linotypeAds = new LinotypeAdsSDK({
    apiKey: "publisher-id",
    timeout: 5000 // Timeout value to preserve latency
});
```

### Run ads in parallel to maximize latency

Provide the most recent user query and any prior context that may be relevant:

```javascript
const adPromise = linotypeAds.getAdForUserQuery(context);
// Run agent code
const adsResponse = await adPromise;
// Display ad
```

### Run ads sequentially to maximize relevance

Provide the most recent agent response and any prior context that may be relevant:

```javascript
const adsResponse = await linotypeAds.getAdForAgentResponse(response);
// Display ad
```

## Important Notes

- **Visual Separation:** We recommend adding a new line between the response and the ad, or displaying the ad in a separate text bubble to maintain clear visual separation.
- **Ad Validation:** Only display an ad if it exists, not if it's an empty string.
- **Markdown Support:** Ensure your display supports markdown so hyperlinks render properly.

## License

Apache 2.0 - see [LICENSE](LICENSE) file for details.
