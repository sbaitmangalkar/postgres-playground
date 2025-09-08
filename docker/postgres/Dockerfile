FROM postgres:16


RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    git \
    postgresql-server-dev-16 \
    postgresql-16-cron \
    ca-certificates \
    wget \
    && rm -rf /var/lib/apt/lists/*

# --- Install pg_graphql ---
# Download the pre-compiled .deb package for Postgres 16.
# Check the pg_graphql releases page on GitHub for the latest version.
RUN wget https://github.com/supabase/pg_graphql/releases/download/v1.5.11/pg_graphql-v1.5.11-pg16-amd64-linux-gnu.deb -O pg_graphql.deb \
    && dpkg -i pg_graphql.deb \
    && rm pg_graphql.deb


WORKDIR /docker-src


RUN git clone https://github.com/michelp/pgjwt.git


WORKDIR /docker-src/pgjwt
RUN make install