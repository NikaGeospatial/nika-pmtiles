# Purpose of this Fork

The original go-pmtiles do not support encoded/unencoded spaces in file paths or a specific bucket naming conventions. This fork ensures that the server logic correctly handle spaces in both:

- File Paths: (e.g., /Internal Data/Maps/)
- File Names: (e.g., City Plan 2024.pmtiles)

This fork is based on protomaps/go-pmtiles v1.30.0.

## Maintenance & Update Workflow

Follow these steps when a new version of upstream (Protomaps) is released.

### 1. Sync with Upstream

First, pull the latest official code into your local environment:

```bash
git checkout main
git fetch upstream
git merge upstream/main
```

### 2. The AI Refactor (The "Nika" Special)

Once the base code is updated, use a coding AI (like Cursor, Claude, or GitHub Copilot) to re-apply the custom logic.

```
# Instructions to AI
Refactor the FileBucket and server (and other parts of the codebase if necessary) to accept spaces within the file path and file names for all the endpoints - get tile, metadata, tilejson
e.g. /{filepath}/{z}/{x}/{y}.mvt

Both filepath and file name must accept spaces.

The frontend will pass encodedURIComponent URL; ensure that it is resolved correctly to the correct bucket location (which is mounted).
```

### 3. Verification and Merge to Production

Verify the fix by testing it locally.

Merge the updated `main` into the stable production `nika-main` branch:

```bash
git checkout nika-main
git merge main
git push origin nika-main
```

# Original Project Info

Below is the original documentation for the base utility.

## go-pmtiles

The single-file utility for creating and working with [PMTiles](https://github.com/protomaps/PMTiles) archives.

## Installation

See [Releases](https://github.com/protomaps/go-pmtiles/releases) for your OS and architecture.

## Docs

See [docs.protomaps.com/pmtiles/cli](https://docs.protomaps.com/pmtiles/cli) for usage.

See [Go package docs](https://pkg.go.dev/github.com/protomaps/go-pmtiles/pmtiles) for API usage.

## Development

Run the program in development:

```sh
go run main.go
```

Run the test suite:

```sh
go test ./pmtiles
```
