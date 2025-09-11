# Start from the official PostgreSQL 16 image
FROM postgres:16

# Install build dependencies and other tools
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    git \
    # cmake is NOT needed for pg_mooncake, but might be for other future extensions
    cmake \
    clang \
    postgresql-server-dev-16 \
    libssl-dev \
    postgresql-16-cron \
    ca-certificates \
    wget \
    && rm -rf /var/lib/apt/lists/*

# --- Install pg_graphql ---
# Download and install the pre-compiled .deb package
RUN wget https://github.com/supabase/pg_graphql/releases/download/v1.5.11/pg_graphql-v1.5.11-pg16-amd64-linux-gnu.deb -O pg_graphql.deb \
    && dpkg -i pg_graphql.deb \
    && rm pg_graphql.deb

# --- Build and install pg_mooncake ---
# This extension uses 'make', not 'cmake'
WORKDIR /docker-src
RUN git clone https://github.com/Mooncake-Labs/pg_mooncake.git

WORKDIR /docker-src/pg_mooncake
RUN make && make install

# --- Build and install pgjwt ---
WORKDIR /docker-src
RUN git clone https://github.com/michelp/pgjwt.git

WORKDIR /docker-src/pgjwt
RUN make install

# Reset WORKDIR to a sensible default if needed
WORKDIR /