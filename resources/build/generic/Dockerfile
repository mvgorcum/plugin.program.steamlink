# Use latest compatible Debian version
FROM debian:bookworm-slim

RUN set -ex \
    && export DEBIAN_FRONTEND=noninteractive \
    && mkdir -p /var/cache/apt/archives \
    && touch /var/cache/apt/archives/lock \
    && apt-get clean \
    && apt-get update -y -q --fix-missing\
    && apt-get upgrade -y \
    && apt-get -y install flatpak bridge-utils libpam-cgfs libvirt0 lxc uidmap dbus-daemon\
    && chmod u+s /usr/bin/bwrap
RUN flatpak remote-add --user --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
RUN flatpak install --noninteractive flathub com.valvesoftware.SteamLink
COPY ./entrypoint.sh /entrypoint.sh


ENTRYPOINT /entrypoint.sh

