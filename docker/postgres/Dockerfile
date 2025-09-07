FROM postgres:16


RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    git \
    postgresql-server-dev-16 \
    postgresql-16-cron \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*


WORKDIR /docker-src


RUN git clone https://github.com/michelp/pgjwt.git


WORKDIR /docker-src/pgjwt
RUN make install