# This file is released under the CC0 1.0 Universal License.
# See the LICENSE file or https://creativecommons.org/publicdomain/zero/1.0/ for details.

ARG os_version="7"
FROM centos:${os_version}
ARG os_version
ARG pwsh_version="7.1.5-1.rhel.${os_version}"

LABEL dev.telitas.project.repository="https://github.com/telitas/powershell-with-pester.docker"
LABEL dev.telitas.base.repository="https://hub.docker.com/_/centos"

RUN yum upgrade -y

# Install powershell
RUN curl https://packages.microsoft.com/config/rhel/${os_version}/prod.repo | tee /etc/yum.repos.d/microsoft.repo
RUN yum install -y powershell-${pwsh_version}

# Install powershell module
SHELL ["pwsh", "-Command"]
RUN Install-Package -Name Pester -Force
RUN Install-Package -Name PSScriptAnalyzer -Force

ENTRYPOINT ["pwsh", "-Command"]
