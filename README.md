# powershell-with-pester.docker

Docker containers for testing PowerShell scripts.

## Description

PowerShell(pwsh) and the following PowerShll modules are installed in each container.

- Pester
- PSScriptAnalyzer

Entry point is `pwsh -Command`.

## Usage

Build image

```sh
docker build --tag pwsh_with_pester /path/to/dockerfile_parent_directory/
```

and run.

```sh
docker run --volume /host/path/to/testee:/mnt/testee --workdir /mnt/testee pwsh_with_pester Invoke-Pester
```

## License

CC0 1.0 Universal

See the LICENSE file or https://creativecommons.org/publicdomain/zero/1.0/ for details.
