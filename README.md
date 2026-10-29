# Dashy for LazyCat

- Upstream: https://github.com/Lissy93/dashy
- Package: `community.lazycat.app.dashy`, first community release 4.9.8.
- Image: `ghcr.io/lissy93/dashy` delivered through `ghcr.1ms.run` with digest verification.
- Target: Linux amd64. Minimum LazyCat OS: 1.6.0 for service `run_as` and persistent owner mapping.
- Persistent data: `/lzcapp/var/user-data` mounted at `/app/user-data`.
- Startup seeds `conf.yml` only when absent or empty. Later edits survive restart and package upgrades.
- Service runs as numeric UID/GID 1000:1000, matching upstream. No root `setup_script`.
- Health check copied from upstream Compose, using `/app/services/healthcheck.js`.
- No file-chooser interception and no `public_path` bypass. Dashboard configuration is shared across users who can access the app.
- Only MiaoMiao community publication is permitted; official-store publication is disabled.

The GitHub workflow smoke-tests the pinned upstream image with a writable UID-1000 data directory, verifies HTTP and upstream health check, and checks config survival across restart. Community publication was enabled after the initial build checks. Run 40823997682 tested the actual 4.9.8 image and published the verified versioned LPK; store application ID 653 is APPROVED, category HomePage (33). LPK SHA256: 89310e5fbbc8feb1983191fdea0df7d13fef0c6f394854cefcb99e41147f4aae.

This is not a LazyCat-device installation test or a complete browser/widget integration test. Dashy's visual editor and third-party widgets have not been end-to-end tested on a LazyCat device.

Existing organization secrets `APPSTORE_URL`, `APPSTORE_TOKEN`, and optional `PRIVATE_STORE_GROUP_CODES` are referenced explicitly, never committed as values.
