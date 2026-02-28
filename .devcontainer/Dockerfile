FROM mcr.microsoft.com/devcontainers/go:1.26

# Install Neovim dependencies and useful tools
RUN apt-get update && apt-get install -y --no-install-recommends \
    gcc \
    g++ \
    make \
    ripgrep \
    fd-find \
    unzip \
    curl \
    git \
    xclip \
    && rm -rf /var/lib/apt/lists/*

# Install latest stable Neovim from GitHub releases
ARG NVIM_VERSION=v0.11.6
RUN curl -fsSL "https://github.com/neovim/neovim/releases/download/${NVIM_VERSION}/nvim-linux-x86_64.tar.gz" \
    | tar xz -C /opt \
    && ln -s /opt/nvim-linux-x86_64/bin/nvim /usr/local/bin/nvim

# Set Neovim as default editor
ENV EDITOR=nvim
ENV VISUAL=nvim

# Install common Go tools (gopls, delve, etc. are already in the base image)
# Install additional useful tools
RUN go install github.com/jackc/pgx/v5@latest 2>/dev/null || true
