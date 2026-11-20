# Atlas3 for chi-tools.uc.edu: the prebuilt Atlas3 dist (chi/build.sh runs the npm
# build on the build machine) served as static files under /atlas/.
# No RUN steps, so the multi-arch legs need no emulation.
FROM docker.io/library/nginx:1.30-alpine@sha256:caf4e1e032a20f9c3c5e28fc7f25ffd768ad8677b4975c54193075997b3a97e3

ARG VERSION=dev
ARG ATLAS_REVISION=unknown
ARG REVISION=unknown
ARG CREATED
LABEL org.opencontainers.image.title="Atlas3 (CHI)" \
      org.opencontainers.image.version="${VERSION}" \
      org.opencontainers.image.revision="${REVISION}" \
      org.opencontainers.image.created="${CREATED}" \
      org.opencontainers.image.source="https://github.com/Center-for-Health-Informatics/Atlas3" \
      edu.uc.chi.atlas3.revision="${ATLAS_REVISION}"

COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY dist/ /usr/share/nginx/html/atlas/
# CHI settings: WebAPI on the same host, sign-in through CHI auth, no plugins.
COPY config-local.json /usr/share/nginx/html/atlas/config-local.json
COPY plugins.json /usr/share/nginx/html/atlas/config/plugins.json
