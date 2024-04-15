FROM aicrowd/meltingpot-challenge:mp-2.2.0-v1 

ENV USER_NAME aicrowd
ENV HOME_DIR /home/$USER_NAME
ENV HOST_UID 1001
ENV HOST_GID 1001

RUN export uid=${HOST_UID} gid=${HOST_GID} && \
    mkdir -p ${HOME_DIR} && \
    echo "$USER_NAME:x:${uid}:${gid}:$USER_NAME,,,:$HOME_DIR:/bin/bash" >> /etc/passwd && \
    echo "$USER_NAME:x:${uid}:" >> /etc/group

RUN chown -R 1001:1001 ${HOME_DIR}

COPY --chown=1001:1001 . ${HOME_DIR}
WORKDIR ${HOME_DIR}

RUN apt -qq update && apt -qq install -y `cat ${HOME_DIR}/apt.txt`

WORKDIR ${HOME_DIR}

RUN pip3 install -r ${HOME_DIR}/requirements.txt && rm -rf /root/.cache

USER ${USER_NAME}

