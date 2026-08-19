# LoonFS Python SDK

Python client for the LoonFS HTTP API.

## Status

This SDK is pre-release. It is not yet published to PyPI. This repository is private until the first release.

## Install

After the first release, install the SDK with:

```sh
pip install loonfs-sdk
```

## Usage

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    base_url="https://api.example.com",
    token="YOUR_TOKEN",
)

capabilities = client.capabilities()
```

`AsyncLoonFS` is the async variant of the client. The optional aiohttp transport
installs with the `aiohttp` extra: `pip install "loonfs-sdk[aiohttp]"`.

## Generated code

The code is generated with Fern from the LoonFS OpenAPI spec (`docs/specs/openapi.json` in `github.com/loonfs/loonfs`). Regeneration runs from the `sdk/fern/` config in that repository (`scripts/generate-sdks.sh`). Do not edit generated files by hand.

See [reference.md](reference.md) for the full API reference.

## License

Apache-2.0
