# This file is released under the CC0 1.0 Universal License.
# See the LICENSE file or https://creativecommons.org/publicdomain/zero/1.0/ for details.

ARG os_version="10"
FROM debian:${os_version}
ARG os_version

LABEL dev.telitas.project.repository="https://github.com/telitas/powershell-with-pester.docker"
LABEL dev.telitas.base.repository="https://hub.docker.com/_/debian"

RUN apt update
RUN apt upgrade

# Install powershell
RUN apt install -y wget
RUN wget https://packages.microsoft.com/config/debian/${os_version}/packages-microsoft-prod.deb
RUN dpkg --install packages-microsoft-prod.deb
RUN apt update
RUN apt install -y powershell

# Install powershell module
SHELL ["pwsh", "-Command"]
RUN Install-Package -Name Pester -Force
RUN Install-Package -Name PSScriptAnalyzer -Force

ENTRYPOINT ["pwsh", "-Command"]
