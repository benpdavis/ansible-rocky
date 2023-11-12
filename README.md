# ansible-rocky
## Windows
### windows - install wsl
`wsl --install`

### windows - reboot and run wsl
`wsl`

### wsl - ubuntu - ansible setup
`sudo apt update`

`sudo apt upgrade`

`sudo apt install ansible`

`sudo apt install sshpass`

### wsl - ubuntu - install additional ansible packages
`ansible-galaxy collection install containers.podman`

`ansible-galaxy collection install community.postgresql`
### wsl - ubuntu - ansible push
`ansible-playbook site.yml -i hosts --ask-pass --ask-become-pass`
### wsl - ubuntu - ansible push with limit
`ansible-playbook site.yml -i hosts --ask-pass --ask-become-pass --limit rocky`
### wsl - ubuntu - ansible push with extra variables
`ansible-playbook site.yml -i hosts --ask-pass --ask-become-pass --extra-vars "upgrade_packages=true expand_fs=true"`
### wsl - ubuntu - turn off ssh key checking
`export ANSIBLE_HOST_KEY_CHECKING=False`
### wsl - ubuntu - turn on ssh key checking
`unset ANSIBLE_HOST_KEY_CHECKING`

## Optional Parameters
`upgrade_packages=true`
`expand_fs=true`
`pginit=true`

## Testing PostgreSQL
User: `user`
Password: `password`

`psql -h raspberrypi4 -U user -W`

## Testing Mosquitto
User: `mosquitto`
Password: `password`

`mosquitto_sub -h raspberrypi4 -t test -u mosquitto -P password`

`mosquitto_pub -h raspberrypi4 -t test -u mosquitto -P password -t test -m test`
