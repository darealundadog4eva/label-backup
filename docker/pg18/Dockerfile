# PostgreSQL 18 compatible variant of resulgg/label-backup
# Upstream ships pg_dump 17.x which is incompatible with PostgreSQL 18.x servers
# Only the database client tools are replaced — original binary is untouched
# Last rebuilt: 2026-05-06

FROM alpine:3.23

RUN apk add --no-cache \
    ca-certificates \
    postgresql18-client \
    mysql-client \
    mongodb-tools \
    redis \
    curl \
    bash

RUN addgroup -g 1001 -S appgroup && \
    adduser -u 1001 -S appuser -G appgroup

RUN mkdir -p /backups && \
    chown -R appuser:appgroup /backups

COPY --from=resulgg/label-backup:latest /label-backup /label-backup

WORKDIR /
RUN pg_dump --version

USER appuser
ENTRYPOINT ["/label-backup"]
