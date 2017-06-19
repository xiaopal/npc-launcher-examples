FROM alpine:3.5

ARG ALPINE_MIRROR=http://mirrors.aliyun.com/alpine
ARG NPC_DL_MIRROR=http://npc.nos-eastchina1.126.net/dl

RUN echo -e "$ALPINE_MIRROR/v3.5/main\n$ALPINE_MIRROR/v3.5/community" >/etc/apk/repositories \
	&& npc_dl_add(){ wget "$NPC_DL_MIRROR/$1" && tar -zx -C /usr/bin -f "$1" && rm -f "$1"; } \
	&& npc_dl_add dumb-init_1.2.0_amd64.tar.gz \
	&& npc_dl_add jq_1.5_linux_amd64.tar.gz \
	&& npc_dl_add serf_0.8.1_linux_amd64.tar.gz
# RUN apk add --no-cache bash

ADD npc-bootstrap.sh /
RUN chmod a+x /npc-bootstrap.sh

ENTRYPOINT ["/npc-bootstrap.sh"]
CMD ["/bin/sh"]