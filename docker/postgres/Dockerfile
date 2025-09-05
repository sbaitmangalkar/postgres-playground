# Use a specific version of Postgres for predictability.
# It's better than using 'latest'. Let's use version 16.
FROM postgres:latest

# Install build dependencies, git, and PostgreSQL development headers
# The specific dev package must match the postgres version (e.g., postgresql-server-dev-16)
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    git \
    postgresql-server-dev-16 \
    && rm -rf /var/lib/apt/lists/*

# Clone, compile, and install the pgjwt extension
RUN git clone https://github.com/michelp/pgjwt.git /docker-src/pgjwt \
    && cd /docker-src/pgjwt \
    && make install