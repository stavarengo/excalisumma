# Build stage
FROM node:24.22.1-alpine AS builder

WORKDIR /app/frontend

# Corepack activates the pnpm version pinned in package.json. The store lives in
# a build cache mount so it never lands in an image layer.
ENV PNPM_HOME=/pnpm COREPACK_ENABLE_DOWNLOAD_PROMPT=0
RUN corepack enable pnpm

# Copy package files first for better caching
COPY frontend/package.json frontend/pnpm-lock.yaml frontend/pnpm-workspace.yaml ./

# Install dependencies
RUN --mount=type=cache,id=pnpm,target=/pnpm/store pnpm install --frozen-lockfile

# Copy source code and config files
COPY frontend/ ./
COPY VERSION ../VERSION

# Build arguments
ARG VITE_APP_BUILD_LABEL
ENV VITE_APP_BUILD_LABEL=$VITE_APP_BUILD_LABEL

# Build the application
RUN pnpm build

# Production stage
FROM nginxinc/nginx-unprivileged:alpine

# Apply Alpine security fixes that may postdate the nginx base image.
# Refresh the package layer when the image's build label changes.
USER root
ARG VITE_APP_BUILD_LABEL
RUN : "${VITE_APP_BUILD_LABEL}" && apk upgrade --no-cache
USER nginx

# Copy nginx config template (will be processed at runtime)
COPY --chown=nginx:nginx --chmod=0444 frontend/nginx.conf.template /etc/nginx/nginx.conf.template

# Copy entrypoint script
COPY --chown=nginx:nginx --chmod=0555 frontend/docker-entrypoint.sh /docker-entrypoint.sh

# Copy built application from builder
COPY --from=builder /app/frontend/dist /usr/share/nginx/html

EXPOSE 80 8080

# Use custom entrypoint to process nginx config template
ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["nginx", "-c", "/tmp/nginx.conf", "-g", "daemon off;"]
