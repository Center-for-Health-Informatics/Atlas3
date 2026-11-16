# CHI build of Atlas3

Files for the Center for Health Informatics' Atlas3 image. They live only on
the `chi/3.0.x` branch of the CHI fork. Upstream work goes on its own branches
off `develop`.

| file | purpose |
| --- | --- |
| `build.sh` | `npm ci && npm run build`, then a multi-arch nginx image built with Apple's `container`; `PUSH=1` scans (trivy), writes an SBOM (syft) and pushes to `chi-tools.uc.edu/atlas3` |
| `CHI_VERSION` | image version; bump for every push (tags are never reused) |
| `Dockerfile`, `nginx.conf` | static `dist/` served under `/atlas/` |
| `config-local.json`, `plugins.json` | CHI settings baked into the image (WebAPI at `/WebAPI`, sign-in on, no plugins) |
| `deploy/compose.yaml` | runs the image on chi-cetus (`/srv/atlas3/compose.yaml`) |

WebAPI's deployment bundle, including chi-hermes's nginx snippet for both
apps, is in the CHI WebAPI fork on `chi/3.0.x` under `chi/deploy/`.

Keeping current with upstream: `git fetch upstream && git merge upstream/develop`.
