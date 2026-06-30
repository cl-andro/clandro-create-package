# Installation

### Contents
- [Dependencies](#Dependencies)
- [Clandro In Android Installation From Repository](#Clandro-In-Android-Installation-From-Repository)
- [Clandro In Android Installation From Source](#Clandro-In-Android-Installation-From-Source)
- [Linux Distros System Installation From Repository](#Linux-Distros-System-Installation-From-Repository)
- [Linux Distros System Installation From Source](#Linux-Distros-System-Installation-From-Source)
##


### Dependencies

- Android users should install [Clandro App](https://github.com/clandro/clandro-app).

- `python3` and optionally `pip3` should be installed in your system.
  - Clandro (non-root shell): `pkg install python`.  Check https://wiki.clandro.com/wiki/Python for details. `pip` will automatically be installed.
  - Linux distros: `sudo apt install python3 python3-pip`.

- The [`ruamel.yaml`](https://yaml.readthedocs.io) python module is used to load `YAML` manifest files. Check [Install](https://yaml.readthedocs.io/en/latest/install.html) instructions for more info.
  - Clandro (non-root shell): `pip install ruamel.yaml`.
  - Linux distros: `sudo pip3 install ruamel.yaml`.
##



### Clandro In Android Installation From Repository

```
pkg install clandro-create-package
```
##



### Clandro In Android Installation From Source

The `clandro-create-package` file should be installed in clandro `bin` directory `/data/data/com.clandro/files/usr/bin`.  
It should have `clandro` `uid:gid` ownership and have readable `700` permission before it can be sourced.  

#### Basic

```
pkg install curl && \
export install_path="/data/data/com.clandro/files/usr/bin" && \
mkdir -p "$install_path" && \
curl -L 'https://github.com/clandro/clandro-create-package/releases/latest/download/clandro-create-package' -o "$install_path/clandro-create-package" && \
export owner="$(stat -c "%u" "$install_path")"; chown "$owner:$owner" "$install_path/clandro-create-package" && \
chmod 700 "$install_path/clandro-create-package";
```

#### Advance

1. Export install directory path and create it.  

```
export install_path="/data/data/com.clandro/files/usr/bin"
mkdir -p "$install_path"
```

2. Download the `clandro-create-package` file.  

    - Download to install directory directly from github using `curl` using a non-root clandro shell.  
        Run `pkg install curl` to install `curl` first.  
        - Latest release:  

          `curl -L 'https://github.com/clandro/clandro-create-package/releases/latest/download/clandro-create-package' -o "$install_path/clandro-create-package"`  

        - Specific release:  

          `curl -L 'https://github.com/clandro/clandro-create-package/releases/download/v0.12.0/clandro-create-package' -o "$install_path/clandro-create-package"`  

        - Master Branch *may be unstable*:  

          `curl -L 'https://github.com/clandro/clandro-create-package/raw/master/src/clandro-create-package' -o "$install_path/clandro-create-package"`  

    - Download `clandro-create-package` file manually from github to the android download directory and then copy it to install directory.  

      You can download the `clandro-create-package` file from a github release from the `Assets` dropdown menu.  

      You can also download it from a specific github branch/tag by opening the [`clandro-create-package`](./src/clandro-create-package) file from the `Code` section.  
      Right-click or hold the `Raw` button at the top and select `Download/Save link`.  

      Then copy the file to install directory using `cat` command below or use a root file browser to manually place it.  

       `cat "/storage/emulated/0/Download/clandro-create-package" > "$install_path/clandro-create-package"`  

3. Set `clandro` ownership and readable permissions.  

    - If you used a `curl` or `cat` to copy the file, then use a non-root clandro shell to set ownership and permissions with `chown` and `chmod` commands respectively:  

      `export owner="$(stat -c "%u" "$install_path")"; chown "$owner:$owner" "$install_path/clandro-create-package" && chmod 700 "$install_path/clandro-create-package";`  

    - If you used a root file browser to copy the file, then use `su` to start a root shell to set ownership and permissions with `chown` and `chmod` commands respectively:  

      `export owner="$(stat -c "%u" "$install_path")"; su -c "chown \"$owner:$owner\" \"$install_path/clandro-create-package\" && chmod 700 \"$install_path/clandro-create-package\"";`  

    - Or manually set them with your root file browser. You can find `clandro` `uid` and `gid` by running the command `id -u` in a non-root clandro shell or by checking the properties of the clandro `bin` directory from your root file browser.  
##





### Linux Distros System Installation From Repository

```
sudo pip3 install clandro-create-package
```
##



### Linux Distros System Installation From Source

The `clandro-create-package` file should be placed in the `/usr/local/bin` directory if you want to install it system-wide for all users as per [FHS 3.0](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch04s09.html).  
It should have readable `755` permission before it can be sourced.  

The install command for `curl`  is for Ubuntu/Debian, it may be different for other distros.  

#### Basic

```
sudo apt install curl && \
export install_path="/usr/local/bin" && \
sudo mkdir -p "$install_path" && \
sudo curl -L 'https://github.com/clandro/clandro-create-package/releases/latest/download/clandro-create-package' -o "$install_path/clandro-create-package" && \
sudo chmod 755 "$install_path/clandro-create-package";
```

#### Advance

1. Export install directory path and create it.  

```
export install_path="/usr/local/bin"
mkdir -p "$install_path"
```

2. Download the `clandro-create-package` file.  

    - Download to install directory directly from github using `curl` using a root shell with `sudo`.  
        Run `sudo apt install curl` to install `curl` first.  

        - Latest release:  

          `sudo curl -L 'https://github.com/clandro/clandro-create-package/releases/latest/download/clandro-create-package' -o "$install_path/clandro-create-package"`  

        - Specific release:  

          `sudo curl -L 'https://github.com/clandro/clandro-create-package/releases/download/v0.12.0/clandro-create-package' -o "$install_path/clandro-create-package"`  

        - Master Branch *may be unstable*:  

          `sudo curl -L 'https://github.com/clandro/clandro-create-package/raw/master/src/clandro-create-package' -o "$install_path/clandro-create-package"`  

    - Download `clandro-create-package` file manually from github to the install directory.  

      You can download the `clandro-create-package` file from a github release from the `Assets` dropdown menu.  

      You can also download it from a specific github branch/tag by opening the [`clandro-create-package`](./src/clandro-create-package) file from the `Code` section.  
      Right-click or hold the `Raw` button at the top and select `Download/Save link`.  

      Then copy the file to install directory using `cat` command below or use a root file browser to manually place it (`sudo nautilus`).  

       `sudo cat "clandro-create-package" > "$install_path/clandro-create-package"`  

3. Set readable permissions.  

    - Set ownership and permissions with `chown` and `chmod` commands respectively:  

      `sudo chmod 755 "$install_path/clandro-create-package"`  
##
