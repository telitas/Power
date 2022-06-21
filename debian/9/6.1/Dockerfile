# This file is released under the CC0 1.0 Universal License.
# See the LICENSE file or https://creativecommons.org/publicdomain/zero/1.0/ for details.

ARG os_version="9"
FROM debian:${os_version}
ARG os_version
ARG pwsh_version="6.1.6-1.debian.${os_version}"

LABEL dev.telitas.project.repository="https://github.com/telitas/powershell-with-pester.docker"
LABEL dev.telitas.base.repository="https://hub.docker.com/_/debian"


# Install powershell
RUN apt-get update && \
    apt-get install -y curl gnupg apt-transport-https && \
    curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add - && \
    sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list' && \
    apt-get update && \
    apt-get install -y powershell=${pwsh_version} && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Install powershell module
SHELL ["pwsh", "-Command"]
RUN $ErrorActionPreference="Stop"; \
    Install-Package -Name Pester -Force; \
    Install-Package -Name PSScriptAnalyzer -Force

ENTRYPOINT ["pwsh", "-Command"]
