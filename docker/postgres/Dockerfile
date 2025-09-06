# Use a specific version tag for reproducible builds.
FROM postgres:16

# Add 'ca-certificates' to the package list
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    git \
    postgresql-server-dev-16 \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Use WORKDIR to create a directory and set it as the working directory.
WORKDIR /docker-src

# Now clone the repository into the current directory (/docker-src)
RUN git clone https://github.com/michelp/pgjwt.git

# Change the working directory into the newly cloned repo and run make install
WORKDIR /docker-src/pgjwt
RUN make install