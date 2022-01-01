ARG os_version="8"
FROM centos:${os_version}
ARG os_version
ARG pwsh_version="7.0.6-1.centos.${os_version}"

LABEL dev.telitas.project.repository="https://github.com/telitas/powershell-with-pester.docker"
LABEL dev.telitas.base.repository="https://hub.docker.com/_/centos"

RUN yum upgrade -y

RUN curl https://packages.microsoft.com/config/rhel/${os_version}/prod.repo | tee /etc/yum.repos.d/microsoft.repo
RUN yum install -y powershell-${pwsh_version}
# Install powershell module
SHELL ["pwsh", "-Command"]
RUN Install-Package -Name Pester -Force
RUN Install-Package -Name PSScriptAnalyzer -Force

ENTRYPOINT ["pwsh", "-Command"]
