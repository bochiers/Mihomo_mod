# Mihomo

Mihomo is a lightweight project containing a prebuilt server binary and a static UI.

## Requirements

- macOS / Linux (prebuilt binaries included).
- No Go toolchain required to run the provided binary.

## Quick start

1. Make the included binary executable:

	`chmod +x mihomo-darwin-arm64-go120-v1.19.17`

2. Run the binary's help to see available flags:

	`./mihomo-darwin-arm64-go120-v1.19.17 --help`

3. Typical start using a configuration file (example):

	`./mihomo-darwin-arm64-go120-v1.19.17 -config config.yaml`

4. Alternatively, you can run the binary in background:

	`nohup ./mihomo-darwin-arm64-go120-v1.19.17 -config config.yaml &`

## Configuration

The root `config.yaml` controls server behavior. An example `config.yaml` (adjust to your build):

```yaml
server:
  listen: ":8080"        # address and port to listen on
  ui_path: "ui"          # path to bundled UI files or externally hosted UI
  geoip_db: "geoip.metadb" # path to GeoIP DB file

log:
  level: "info"          # debug, info, warn, error

tls:
  enabled: false
  cert: ""
  key: ""
```

- Place `config.yaml` next to the binary (or pass a full path when starting).
- If the binary supports different flag names, run `--help` to confirm exact flags.

## UI

- The `ui/` directory contains a static web UI (see `ui/index.html`).
- If the server binary can serve static assets, point `ui_path` in `config.yaml` to `./ui`.
- You can also serve `ui/` separately (e.g., with `nginx` or a simple static file server) and point the server to the API endpoint.

## GeoIP database

- `geoip.metadb` (present in the repository) is the GeoIP database used by the server. Keep it next to the binary or set the correct path in `config.yaml`.

## Running as a service

- On Linux, create a systemd service that runs the binary with `-config /path/to/config.yaml`.
- On macOS, use `launchd` or a process manager of your choice.

## Troubleshooting

- Check file permissions (`chmod`) for the binary and data files.
- Inspect logs or run with higher log level to diagnose issues.
- Use `--help` on the binary to find supported command-line flags.

## Files of interest

- [config.yaml](config.yaml)
- [geoip.metadb](geoip.metadb)
- ui/ (static UI files)
- mihomo-darwin-arm64-go120-v1.19.17 (prebuilt binary)

## Contact

If you need further help, open an issue or contact the maintainer.

# Mihomo_mod
