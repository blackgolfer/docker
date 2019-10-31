FROM archlinux/base

# installing pkgfile and pacstrap
RUN pacman -Sy --noconfirm && \
    pacman -S --noconfirm pkgfile && \
    pkgfile --update && \
    pkgfile pacstrap && \
    pacman -S --noconfirm extra/arch-install-scripts

# RUN useradd -m yay
# RUN pacman -Syuq --needed --noconfirm
# RUN pacman -Sq --needed --noconfirm git go sudo base-devel
# RUN mkdir -p /opt/Workspace
# RUN chown -R yay.yay /opt/Workspace

# RUN printf 'yay ALL=(ALL) NOPASSWD: ALL\n' | tee -a /etc/sudoers

# USER yay
# RUN git clone https://aur.archlinux.org/yay.git /opt/Workspace/yay
# RUN cd /opt/Workspace/yay && makepkg -si --noconfirm

# CMD ["/usr/lib/systemd/systemd"]

# installing yay
RUN echo '[multilib]' >> /etc/pacman.conf && \
    echo 'Include = /etc/pacman.d/mirrorlist' >> /etc/pacman.conf && \
    pacman --noconfirm -Syyu && \
    pacman --noconfirm -S base-devel git && \
    useradd -m -r -s /bin/bash aur && \
    passwd -d aur && \
    echo 'aur ALL=(ALL) ALL' > /etc/sudoers.d/aur && \
    mkdir -p /home/aur/.gnupg && \
    echo 'standard-resolver' > /home/aur/.gnupg/dirmngr.conf && \
    chown -R aur:aur /home/aur && \
    mkdir /build && \
    chown -R aur:aur /build && \
    cd /build && \
    sudo -u aur git clone --depth 1 https://aur.archlinux.org/yay.git && \
    cd yay && \
    sudo -u aur makepkg --noconfirm -si && \
    sudo -u aur yay --afterclean --removemake --save && \
    pacman -Qtdq | xargs -r pacman --noconfirm -Rcns && \
    rm -rf /home/aur/.cache && \
    rm -rf /build

#CMD ["/bin/bash"]