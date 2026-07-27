[UV_ASTRAL_MIRROR_URL](https://docs.astral.sh/uv/reference/environment/#uv_astral_mirror_url)

替换所有 Astral 镜像元数据和工件下载的基础 URL `https://releases.astral.sh`。设置后，uv 将仅使用配置的镜像 URL，不会回退到 GitHub 或原始 GitHub 地址。URL 中的路径部分会被保留：仅在附加正常路径后缀（例如 `/github/versions/main/v1/uv.ndjson`）之前去除尾部斜杠。这对代理仓库（例如 Artifactory、Nexus）镜像 `releases.astral.sh` 很有用。更具体的源具有更高优先级：`UV_PYTHON_INSTALL_MIRROR` 和 `python-install-mirror` 会覆盖此变量用于 CPython 下载，而 `UV_INSTALLER_GITHUB_BASE_URL` 和 `UV_INSTALLER_GHE_BASE_URL` 会覆盖此变量用于 uv 自身更新。

Replaces the https://releases.astral.sh base URL for all Astral-mirrored metadata and artifact downloads.

When set, uv uses only the configured mirror URL and does not fall back to GitHub or raw GitHub. Path components in the URL are preserved: only trailing slashes are trimmed before appending the normal path suffix (e.g., /github/versions/main/v1/uv.ndjson).

This is useful for proxy repositories (e.g., Artifactory, Nexus) that mirror releases.astral.sh.

More-specific sources take precedence: UV_PYTHON_INSTALL_MIRROR and python-install-mirror override this variable for CPython downloads, while UV_INSTALLER_GITHUB_BASE_URL and UV_INSTALLER_GHE_BASE_URL override this variable for uv self update.

---

# [UV_CACHE_DIR](https://docs.astral.sh/uv/reference/environment/#uv_cache_dir)

相当于命令行参数 `--cache-dir`。设置后，uv 将使用此目录代替默认缓存目录进行缓存。

Equivalent to the --cache-dir command-line argument. If set, uv will use this directory for caching instead of the default cache directory.

---

# [UV_CONFIG_FILE](https://docs.astral.sh/uv/reference/environment/#uv_config_file)

相当于命令行参数 `--config-file`。期望一个本地 `uv.toml` 文件的路径，用作配置文件。

Equivalent to the --config-file command-line argument. Expects a path to a local uv.toml file to use as the configuration file.

---

[UV_CREDENTIALS_DIR](https://docs.astral.sh/uv/reference/environment/#uv_credentials_dir)

使用纯文本后端存储凭据的目录。

The directory for storage of credentials when using a plain text backend.

---

# [UV_INSTALL_DIR](https://docs.astral.sh/uv/reference/environment/#uv_install_dir)

使用独立安装程序以及自身更新功能安装 uv 的目录。默认指向 `~/.local/bin`。

The directory in which to install uv using the standalone installer and self update feature. Defaults to ~/.local/bin.

---

[UV_NO_CONFIG](https://docs.astral.sh/uv/reference/environment/#uv_no_config)

相当于命令行参数 `--no-config`。如果设置，uv 将不会读取当前目录、父目录或用户配置目录中的任何配置文件。

Equivalent to the --no-config command-line argument. If set, uv will not read any configuration files from the current directory, parent directories, or user configuration directories.

---

[UV_NO_GITHUB_FAST_PATH](https://docs.astral.sh/uv/reference/environment/#uv_no_github_fast_path)

禁用 GitHub 特定请求，这些请求允许 uv 在某些情况下跳过 `git fetch`。

Disable GitHub-specific requests that allow uv to skip git fetch in some circumstances.

---

[UV_NO_INSTALLER_LOCAL](https://docs.astral.sh/uv/reference/environment/#uv_no_install_local)

相当于命令行参数 `--no-install-local`。如果设置，uv 将跳过当前项目、工作区成员以及任何其他本地（路径或可编辑）包，仅安装远程依赖。

Equivalent to the --no-install-local command-line argument. If set, uv will skip the current project, workspace members, and any other local (path or editable) packages, installing only remote dependencies.

---

[UV_NO_INSTALLER_METADATA](https://docs.astral.sh/uv/reference/environment/#uv_no_installer_metadata)

跳过将 uv 安装程序元数据文件（例如 `INSTALLER`、`REQUESTED` 和 `direct_url.json`）写入 `site-packages` 的 `.dist-info` 目录。

Skip writing uv installer metadata files (e.g., INSTALLER, REQUESTED, and direct_url.json) to site-packages .dist-info directories.

---

[UV_NO_MODIFY_PATH](https://docs.astral.sh/uv/reference/environment/#uv_no_modify_path)

当使用独立安装程序及自身更新功能安装 uv 时，避免修改 `PATH` 环境变量。为向后兼容，也支持 `INSTALLER_NO_MODIFY_PATH` 作为别名。

Avoid modifying the PATH environment variable when installing uv using the standalone installer and self update feature. INSTALLER_NO_MODIFY_PATH is also supported as an alias, for backwards compatibility.

---

[UV_PROJECT_ENVIRONMENT](https://docs.astral.sh/uv/reference/environment/#uv_project_environment)

指定项目虚拟环境所用目录的路径。

Specifies the path to the directory to use for a project virtual environment.

---

[UV_PYPY_INSTALL_MIRROR](https://docs.astral.sh/uv/reference/environment/#uv_pypy_install_mirror)

受管理的 PyPy 安装从 `python.org` 下载。此变量可设置为镜像 URL，以用于 PyPy 安装的替代源。提供的 URL 将替换 `https://downloads.python.org/pypy`，例如在 `https://downloads.python.org/pypy/pypy3.8-v7.3.7-osx64.tar.bz2` 中。通过使用 `file://` URL 方案，可以从本地目录读取发行包。

Managed PyPy installations are downloaded from python.org.

This variable can be set to a mirror URL to use a different source for PyPy installations. The provided URL will replace https://downloads.python.org/pypy in, e.g., https://downloads.python.org/pypy/pypy3.8-v7.3.7-osx64.tar.bz2. Distributions can be read from a local directory by using the file:// URL scheme.

---

# [UV_PYTHON](https://docs.astral.sh/uv/reference/environment/#uv_python)

相当于命令行参数 `--python`。如果设置为路径，uv 将在所有操作中使用此 Python 解释器。

Equivalent to the --python command-line argument. If set to a path, uv will use this Python interpreter for all operations.

---

# [UV_PYTHON_BIN_DIR](https://docs.astral.sh/uv/reference/environment/#uv_python_bin_dir)

指定用于放置已安装的受管理 Python 可执行文件链接的目录。

Specifies the directory to place links to installed, managed Python executables.

---

# [UV_PYTHON_CACHE_DIR](https://docs.astral.sh/uv/reference/environment/#uv_python_cache_dir)

指定在安装之前缓存受管理的 Python 安装档案的目录。

Specifies the directory for caching the archives of managed Python installations before installation.

---

[UV_PYTHON_DOWNLOADS_JSON_URL](https://docs.astral.sh/uv/reference/environment/#uv_python_downloads_json_url)

受管理的 Python 安装信息硬编码在 uv 二进制文件中。此变量可设置为指向 JSON Python 安装列表的本地路径或 URL，以覆盖硬编码列表。这允许自定义下载 URL，或使用比此版本 uv 硬编码的 Python 版本稍旧或稍新的版本。

Managed Python installations information is hardcoded in the uv binary.

This variable can be set to a local path or URL pointing to a JSON list of Python installations to override the hardcoded list.

This allows customizing the URLs for downloads or using slightly older or newer versions of Python than the ones hardcoded into this build of uv.

---

# [UV_PYTHON_INSTALL_BIN](https://docs.astral.sh/uv/reference/environment/#uv_python_install_bin)  <!-- 已修正链接（原为 isntall） -->

是否将 Python 可执行文件安装到 `UV_PYTHON_BIN_DIR` 目录中。

Whether to install the Python executable into the UV_PYTHON_BIN_DIR directory.

---

# [UV_PYTHON_INSTALL_DIR](https://docs.astral.sh/uv/reference/environment/#uv_python_install_dir)

指定用于存储受管理的 Python 安装的目录。

Specifies the directory for storing managed Python installations.

---

[UV_PYTHON_INSTALL_MIRROR](https://docs.astral.sh/uv/reference/environment/#uv_python_install_mirror)

受管理的 Python 安装从 Astral 的 `python-build-standalone` 项目下载。此变量可设置为镜像 URL，以用于 Python 安装的替代源。提供的 URL 将替换 `https://github.com/astral-sh/python-build-standalone/releases/download`，例如在 `https://github.com/astral-sh/python-build-standalone/releases/download/20240713/cpython-3.12.4%2B20240713-aarch64-apple-darwin-install_only.tar.gz` 中。通过使用 `file://` URL 方案，可以从本地目录读取发行包。此更具体的镜像对于 CPython 下载优先于 `UV_ASTRAL_MIRROR_URL`。

Managed Python installations are downloaded from the Astral python-build-standalone project.

This variable can be set to a mirror URL to use a different source for Python installations. The provided URL will replace https://github.com/astral-sh/python-build-standalone/releases/download in, e.g., https://github.com/astral-sh/python-build-standalone/releases/download/20240713/cpython-3.12.4%2B20240713-aarch64-apple-darwin-install_only.tar.gz. Distributions can be read from a local directory by using the file:// URL scheme.

This more-specific mirror takes precedence over UV_ASTRAL_MIRROR_URL for CPython downloads.

---

# [UV_PYTHON_SEARCH_PATH](https://docs.astral.sh/uv/reference/environment/#uv_python_search_path)

用于覆盖 `PATH` 以进行 Python 可执行文件发现。当设置时，uv 将在此变量指定的目录中搜索 Python 解释器，而不是在 `PATH` 中搜索。

Used to override PATH for Python executable discovery.

When set, uv will search for Python interpreters in the directories specified by this variable instead of PATH.

---

[UV_RESOLUTION](https://docs.astral.sh/uv/reference/environment/#uv_resolution)

相当于命令行参数 `--resolution`。例如，如果设置为 `lowest-direct`，uv 将安装所有直接依赖的最低兼容版本。

Equivalent to the --resolution command-line argument. For example, if set to lowest-direct, uv will install the lowest compatible versions of all direct dependencies.

---

# [UV_SYSTEM_PYTHON](https://docs.astral.sh/uv/reference/environment/#uv_system_python)

相当于命令行参数 `--system`。如果设置为 `true`，uv 将使用系统 `PATH` 中找到的第一个 Python 解释器。警告：`UV_SYSTEM_PYTHON=true` 旨在用于持续集成（CI）或容器化环境，应谨慎使用，因为修改系统 Python 可能导致意外行为。

Equivalent to the --system command-line argument. If set to true, uv will use the first Python interpreter found in the system PATH.

WARNING: UV_SYSTEM_PYTHON=true is intended for use in continuous integration (CI) or containerized environments and should be used with caution, as modifying the system Python can lead to unexpected behavior.

---

# [UV_TOOL_BIN_DIR](https://docs.astral.sh/uv/reference/environment/#uv_tool_bin_dir)

指定用于安装工具可执行文件的“bin”目录。

Specifies the "bin" directory for installing tool executables.

---

# [UV_TOOL_DIR](https://docs.astral.sh/uv/reference/environment/#uv_tool_dir)

指定 uv 存储受管理工具的目录。

Specifies the directory where uv stores managed tools.

---

# [UV_UNMANAGED_INSTALL](https://docs.astral.sh/uv/reference/environment/#uv_unmanaged_install)

用于临时环境（如 CI）将 uv 安装到特定路径，同时防止安装程序修改 shell 配置文件或环境变量。

Used ephemeral environments like CI to install uv to a specific path while preventing the installer from modifying shell profiles or environment variables.

---

[UV_VENV_CLEAR](https://docs.astral.sh/uv/reference/environment/#uv_venv_clear)  <!-- 已修正链接（原为 vene） -->

相当于命令行参数 `--clear`。如果设置，uv 将删除目标路径中的任何现有文件或目录。

Equivalent to the --clear command-line argument. If set, uv will remove any existing files or directories at the target path.

---

[UV_WORKING_DIR](https://docs.astral.sh/uv/reference/environment/#uv_working_dir)

相当于命令行参数 `--directory`。为向后兼容，也支持 `UV_WORKING_DIRECTORY`（自 v0.9.1 添加）。

Equivalent to the --directory command-line argument. UV_WORKING_DIRECTORY (added in v0.9.1) is also supported for backwards compatibility.

---

# [APPDATA](https://docs.astral.sh/uv/reference/environment/#appdata)

Windows 系统上用户级配置目录的路径。

Path to user-level configuration directory on Windows systems.

---

[COLUMNS](https://docs.astral.sh/uv/reference/environment/#columns)

覆盖用于换行的终端宽度。此变量不由 uv 直接读取。这是一个准标准变量，参见例如 ncurses(3x) 中的描述。

Overrides terminal width used for wrapping. This variable is not read by uv directly.

This is a quasi-standard variable, described, e.g., in ncurses(3x).

---

# [CONDA_PREFIX](https://docs.astral.sh/uv/reference/environment/#conda_prefix)

用于检测活动 Conda 环境的路径。

Used to detect the path of an active Conda environment.

---

# [PATH](https://docs.astral.sh/uv/reference/environment/#path)

标准 `PATH` 环境变量。

The standard PATH env var.

---

# [PSModulePath](https://docs.astral.sh/uv/reference/environment/#psmodulepath)

用于检测 PowerShell 的使用（由 PowerShell 在所有平台上设置）。

Used to detect PowerShell usage (set by PowerShell on all platforms).

---

# [PYTHONPATH](https://docs.astral.sh/uv/reference/environment/#pythonpath)

将目录添加到 Python 模块搜索路径（例如 `PYTHONPATH=/path/to/modules`）。

Adds directories to Python module search path (e.g., PYTHONPATH=/path/to/modules).

---

[PYX_CREDENTIALS_DIR](https://docs.astral.sh/uv/reference/environment/#pyx_credentials_dir)

指定 uv 存储 `pyx` 凭据的目录。

Specifies the directory where uv stores pyx credentials.

---

# [ruff](https://docs.astral.sh/uv/reference/environment/#ruff)

`uv format` 使用的 Ruff 二进制文件的路径。

The path to the Ruff binary used by uv format.

---

[SSL_CERT_DIR](https://docs.astral.sh/uv/reference/environment/#ssl_cert_dir)

包含 PEM 编码的 CA 证书文件的目录路径，用于 TLS 连接。支持多个条目，使用平台特定的分隔符（Unix 上为 `:`，Windows 上为 `;`）。证书通常使用 `.pem`、`.crt` 或 `.cer` 扩展名存储，但 uv 会尝试从提供的 `SSL_CERT_DIR` 中的任何常规文件读取证书。无法解析为 PEM 证书的文件将被忽略。uv 会解析符号链接并忽略悬空的符号链接。仅支持 PEM 编码文件，即不支持 DER 编码文件。当设置时，这将覆盖默认证书源（捆绑的 Mozilla 根证书或系统证书）。仅此目录中的证书将被信任。

Path to a directory containing PEM-encoded CA certificate files for TLS connections.

Multiple entries are supported, separated using a platform-specific delimiter (: on Unix, ; on Windows).

Certificates are usually stored with .pem, .crt, or .cer extensions, but uv will attempt to read a certificate from any regular file in the provided SSL_CERT_DIR.

Files that cannot be parsed as PEM certificates are ignored. uv resolves symlinks and ignores dangling symlinks.

Only PEM-encoded files are supported, i.e., DER-encoded files are not supported.

When set, this overrides the default certificate source (bundled Mozilla roots or system certificates). Only the certificates in this directory will be trusted.

---

[SSL_CERT_FILE](https://docs.astral.sh/uv/reference/environment/#ssl_cert_file)

CA 证书捆绑文件的路径，用于 TLS 连接。需要一个 PEM 编码的证书文件（例如 `certs.pem`、`ca-bundle.crt`）。不支持 DER 编码文件。当设置时，这将覆盖默认证书源（捆绑的 Mozilla 根证书或系统证书）。仅此文件中的证书将被信任。

Path to a CA certificate bundle file for TLS connections.

Requires a PEM-encoded certificate file (e.g., certs.pem, ca-bundle.crt). DER-encoded files are not supported.

When set, this overrides the default certificate source (bundled Mozilla roots or system certificates). Only the certificates in this file will be trusted.

---

# [SYSTEMDRIVE](https://docs.astral.sh/uv/reference/environment/#systemdrive)

Windows 系统上系统级配置目录的路径。

Path to system-level configuration directory on Windows systems.

---

[TY](https://docs.astral.sh/uv/reference/environment/#ty)

`uv check` 使用的 `ty` 二进制文件的路径。

The path to the ty binary used by uv check.

---

# [USERPROFILE](https://docs.astral.sh/uv/reference/environment/#userprofile)

Windows 系统上用户配置文件根目录的路径。

Path to root directory of user's profile on Windows systems.

---

[UV](https://docs.astral.sh/uv/reference/environment/#uv)

用于调用 uv 的二进制文件路径。此变量会传播给 uv 生成的所有子进程。如果通过符号链接调用可执行文件，某些平台将返回符号链接的路径，而其他平台将返回符号链接目标的路径。安全注意事项请参见 https://doc.rust-lang.org/std/env/fn.current_exe.html#security。

The path to the binary that was used to invoke uv.

This is propagated to all subprocesses spawned by uv.

If the executable was invoked through a symbolic link, some platforms will return the path of the symbolic link and other platforms will return the path of the symbolic link’s target.

See https://doc.rust-lang.org/std/env/fn.current_exe.html#security for security considerations.

---

# [XDG_BIN_HOME](https://docs.astral.sh/uv/reference/environment/#xdg_bin_home)

可执行文件安装目录的路径。

Path to directory where executables are installed.

---

# [XDG_CACHE_HOME](https://docs.astral.sh/uv/reference/environment/#xdg_cache_home)

Unix 系统上缓存目录的路径。

Path to cache directory on Unix systems.

---

# [XDG_CONFIG_DIRS](https://docs.astral.sh/uv/reference/environment/#xdg_config_dirs)

Unix 系统上系统级配置目录的路径。

Path to system-level configuration directory on Unix systems.

---

# [XDG_CONFIG_HOME](https://docs.astral.sh/uv/reference/environment/#xdg_config_home)

Unix 系统上用户级配置目录的路径。

Path to user-level configuration directory on Unix systems.

---

# [XDG_DATA_HOME](https://docs.astral.sh/uv/reference/environment/#xdg_data_home)

用于存储受管理的 Python 安装和工具的目录路径。

Path to directory for storing managed Python installations and tools.

---

# [ZDOTDIR](https://docs.astral.sh/uv/reference/environment/#zdotdir)

用于在使用 Zsh 时确定使用哪个 `.zshenv` 文件。

Used to determine which .zshenv to use when Zsh is being used.