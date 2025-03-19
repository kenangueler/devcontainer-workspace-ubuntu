FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

ARG REMOTE_USER
ARG REMOTE_UID
ARG REMOTE_GID

RUN <<EOF
  passwd -d root
  userdel -fr ubuntu || true && groupdel ubuntu || true
  userdel -fr ${REMOTE_USER} || true && groupdel ${REMOTE_USER} || true
  groupadd --gid ${REMOTE_GID} ${REMOTE_USER}
  useradd -m --uid ${REMOTE_UID} --gid ${REMOTE_GID} -G sudo ${REMOTE_USER}
  echo "${REMOTE_USER} ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
  usermod -s /bin/zsh root
EOF