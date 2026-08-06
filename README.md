# ifttt-action

<p align="left">
  <a href="https://github.com/screendriver/ifttt-action"><img alt="GitHub Actions status" src="https://github.com/screendriver/ifttt-action/workflows/CI/badge.svg"></a>
</p>

A GitHub action that triggers an [IFTTT webhooks](https://ifttt.com/maker_webhooks)
event. This is useful for example when you want to trigger a IFTTT webhook after
your deployment succeeds.

## Usage

See [action.yml](https://github.com/screendriver/ifttt-action/blob/master/action.yml)

```yaml
steps:
  - uses: screendriver/ifttt-action@v1
    with:
      event: your-webhook-event
      key: your-webhook-secret-key
```

## Privacy

This Action contacts Chainguard's licensing server to verify authorization. Connection metadata (IP address, GitHub repository identifier, timestamp, and any metadata encoded in the auth token) is transmitted to Chainguard, Inc. even if authorization is denied in accordance with our [Privacy Notice](https://www.chainguard.dev/legal/privacy-notice)
