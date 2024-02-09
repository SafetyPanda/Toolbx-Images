# Toolbx-Images
Personal Images for Development containers, feel free to use for whatever or as reference!

# How to Use
Build Image:

`podman build . -t $USER/<toolbx-foldername>:latest`

Toolbox Create:

`toolbox create -c <container_name> -i $USER/<toolbx-foldername>`

Now you can enter!

# How I use with VS-Code
I've already added the SSH Server settings so you can SSH into from VSCode into the Container File.

On the same system the VSCode is installed either create a systemd service file to `$HOME/.config/systemd/user/toolbox_ssh.service`:

``` [Unit]
Description=Launch sshd in Fedora Toolbox

[Service]
Type=longrun
ExecPre=/usr/bin/podman start <container_name>
ExecStart=/usr/bin/toolbox run sudo /usr/sbin/sshd -D

[Install]
WantedBy=default.target 

```

Or in a seperate terminal run:

`toolbox run -c <container_name> sudo /usr/sbin/sshd -D &`