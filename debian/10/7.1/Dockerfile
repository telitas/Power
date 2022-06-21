# This file is released under the CC0 1.0 Universal License.
# See the LICENSE file or https://creativecommons.org/publicdomain/zero/1.0/ for details.

ARG os_version="10"
FROM debian:${os_version}
ARG os_version
ARG pwsh_version="7.1.5-1.debian.${os_version}"

LABEL dev.telitas.project.repository="https://github.com/telitas/powershell-with-pester.docker"
LABEL dev.telitas.base.repository="https://hub.docker.com/_/debian"

# Install powershell
RUN apt-get update && \
    apt-get install -y wget && \
    wget https://packages.microsoft.com/config/debian/${os_version}/packages-microsoft-prod.deb && \
    dpkg --install packages-microsoft-prod.deb && \
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
