FROM blackgolfer/archlinux

ARG PROFILE_NAME=xfce

ADD ./iso-profiles /iso-profiles
RUN yay -S pamac-aur
RUN pamac install manjaro-tools-iso

RUN buildiso -f -p $PROFILE_NAME -b stable

RUN rm -r /var/lib/manjaro-tools/buildiso/