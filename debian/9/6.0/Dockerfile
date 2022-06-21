# This file is released under the CC0 1.0 Universal License.
# See the LICENSE file or https://creativecommons.org/publicdomain/zero/1.0/ for details.

ARG os_version="9"
FROM debian:${os_version}
ARG os_version
ARG pwsh_version="6.0.5-1.debian.${os_version}"

LABEL dev.telitas.project.repository="https://github.com/telitas/powershell-with-pester.docker"
LABEL dev.telitas.base.repository="https://hub.docker.com/_/debian"

RUN apt update
RUN apt upgrade

# Install powershell
RUN apt install -y curl gnupg apt-transport-https
RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
RUN sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'
RUN apt update
RUN apt install -y powershell=${pwsh_version}

# Install powershell module
SHELL ["pwsh", "-Command"]
RUN Install-Package -Name Pester -Force
RUN Install-Package -Name PSScriptAnalyzer -Force

ENTRYPOINT ["pwsh", "-Command"]
