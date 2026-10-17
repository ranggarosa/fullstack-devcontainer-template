# Ganti 8.3 menjadi 8.4 jika ingin beralih ke PHP 8.4.
FROM mcr.microsoft.com/devcontainers/php:1-8.3-bookworm

# Remove the stale Yarn APT entry before Dev Container features run apt-get update.
RUN for source in /etc/apt/sources.list /etc/apt/sources.list.d/*.list; do \
        if [ -f "$source" ]; then \
            sed -i '/dl.yarnpkg.com\/debian/d' "$source"; \
        fi; \
    done && \
    for source in /etc/apt/sources.list.d/*.sources; do \
        if [ -f "$source" ] && grep -qF 'dl.yarnpkg.com/debian' "$source"; then \
            awk 'BEGIN { RS = ""; ORS = "\n\n" } !/dl.yarnpkg.com\/debian/' "$source" > "$source.tmp" && \
                mv "$source.tmp" "$source"; \
        fi; \
    done
