# Releasing

SDK v0.2.x targets LoonFS API v0.3.x.

Before the first release, add a PyPI Trusted Publisher to the existing `loonfs`
project for:

- owner: `loonfs`
- repository: `loonfs-sdk-python`
- workflow: `release.yml`
- environment: `pypi`

The GitHub environment should require a maintainer's approval. Build and inspect
the distribution locally before publishing:

```sh
python -m pip install build twine
python -m build
python -m twine check dist/*
```

Create and push the matching `vX.Y.Z` tag, then run the **Publish package**
workflow with that tag. The workflow builds the wheel and source distribution,
checks their metadata, and publishes them through PyPI Trusted Publishing.
