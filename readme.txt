super super basic smokeping

basically i don't even have this running in systemd.

I have a proxy nginx, config is in "nginx" directory.  very basic.

I just run PODMAN_START
On the machine this repo is checked out at $HOME/task/smokeping (that is hardcoded in the script)
And I am uid 1000

I tag the image as "deployed" in case I randomly pulled another one, the script runs "deployed".  Obviously I did not pull another image:

lscr.io/linuxserver/smokeping    latest      90f5658c6bc7  19 months ago  225 MB
localhost/smokeping              deployed    90f5658c6bc7  19 months ago  225 MB

this is podman image inspect on the image -- note the real docker digest is the "Digest" -- "Id" is something that is mostly podman-internal.

latest would probably work fine, just including for reference


[
     {
          "Id": "90f5658c6bc720ef69541916ae6fab633c97721e6c5d6c9be40f858bbe60d3d9",
          "Digest": "sha256:65b3dd6ea3b4ba8a7ef7096e8ba6f92b43a2c69732ca856d73ee1407016b1882",
          "RepoTags": [
               "localhost/smokeping:deployed",
               "lscr.io/linuxserver/smokeping:latest"
          ],
          "RepoDigests": [
               "localhost/smokeping@sha256:65b3dd6ea3b4ba8a7ef7096e8ba6f92b43a2c69732ca856d73ee1407016b1882",
               "localhost/smokeping@sha256:7b3f38b3c21a29c99033840f9af5a19c66e197d19897f6ce10f71a355701470f",
               "lscr.io/linuxserver/smokeping@sha256:65b3dd6ea3b4ba8a7ef7096e8ba6f92b43a2c69732ca856d73ee1407016b1882",
               "lscr.io/linuxserver/smokeping@sha256:7b3f38b3c21a29c99033840f9af5a19c66e197d19897f6ce10f71a355701470f"
          ],
          "Parent": "",
          "Comment": "buildkit.dockerfile.v0",
          "Created": "2025-02-25T20:41:01.936163446Z",
          "Config": {
               "ExposedPorts": {
                    "80/tcp": {}
               },
               "Env": [
                    "PATH=/lsiopy/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                    "PS1=$(whoami)@$(hostname):$(pwd)\\$ ",
                    "HOME=/root",
                    "TERM=xterm",
                    "S6_CMD_WAIT_FOR_SERVICES_MAXTIME=0",
                    "S6_VERBOSITY=1",
                    "S6_STAGE2_HOOK=/docker-mods",
                    "VIRTUAL_ENV=/lsiopy",
                    "LSIO_FIRST_PARTY=true"
               ],
               "Entrypoint": [
                    "/init"
               ],
               "Volumes": {
                    "/config": {},
                    "/data": {}
               },
               "WorkingDir": "/",
               "Labels": {
                    "build_version": "Linuxserver.io version:- 2.8.2-r3-ls123 Build-date:- 2025-02-25T20:36:45+00:00",
                    "maintainer": "notdriz",
                    "org.opencontainers.image.authors": "linuxserver.io",
                    "org.opencontainers.image.created": "2025-02-25T20:36:45+00:00",
                    "org.opencontainers.image.description": "[Smokeping](https://oss.oetiker.ch/smokeping/) keeps track of your network latency. For a full example of what this application is capable of visit [UCDavis](http://smokeping.ucdavis.edu/cgi-bin/smokeping.fcgi).",
                    "org.opencontainers.image.documentation": "https://docs.linuxserver.io/images/docker-smokeping",
                    "org.opencontainers.image.licenses": "GPL-3.0-only",
                    "org.opencontainers.image.ref.name": "bf549a76f8bb1d9c573deca5071859a290a9bcb4",
                    "org.opencontainers.image.revision": "bf549a76f8bb1d9c573deca5071859a290a9bcb4",
                    "org.opencontainers.image.source": "https://github.com/linuxserver/docker-smokeping",
                    "org.opencontainers.image.title": "Smokeping",
                    "org.opencontainers.image.url": "https://github.com/linuxserver/docker-smokeping/packages",
                    "org.opencontainers.image.vendor": "linuxserver.io",
                    "org.opencontainers.image.version": "2.8.2-r3-ls123"
               }
          },
          "Version": "",
          "Author": "",
          "Architecture": "amd64",
          "Os": "linux",
          "Size": 224874699,
          "VirtualSize": 224874699,
          "GraphDriver": {
               "Name": "overlay",
               "Data": {
                    "LowerDir": "/home/joe/.local/share/containers/storage/overlay/5f76d74bb742ad24b941681c8786da4ce3b3d8c394d064ab5dd18e0cc9bb5d92/diff:/home/joe/.local/share/containers/storage/overlay/427b66d1e96d6210cfa6632d6d7daf7500f602274ac0abebb36c933d0becd16b/diff:/home/joe/.local/share/containers/storage/overlay/474cb5ce2c1ce5f586c91c8398912419d3cf6a17da5c7db1aeb7960c9e2be993/diff:/home/joe/.local/share/containers/storage/overlay/598874fd2ee6a77fc61e8fc28da17521157e589bedba05d0d9cdaa56502a45ed/diff:/home/joe/.local/share/containers/storage/overlay/06bbc714b09c139625bafb1baf94c128291f53095232064ee7730249595cc107/diff:/home/joe/.local/share/containers/storage/overlay/61e34beabfe1a6bdfeabae54d6aef3d39b851ef439b45bcfa462f8106c005beb/diff:/home/joe/.local/share/containers/storage/overlay/539e98ca9b9abf7f24f52146e5d9a60cd878b9c798fa1e8786f8ca0a91ff5e02/diff",
                    "UpperDir": "/home/joe/.local/share/containers/storage/overlay/e9ce325bfca5265d9e96ce3e9386fa754195d28acfd20bb2188d0e640fbbd5b8/diff",
                    "WorkDir": "/home/joe/.local/share/containers/storage/overlay/e9ce325bfca5265d9e96ce3e9386fa754195d28acfd20bb2188d0e640fbbd5b8/work"
               }
          },
          "RootFS": {
               "Type": "layers",
               "Layers": [
                    "sha256:539e98ca9b9abf7f24f52146e5d9a60cd878b9c798fa1e8786f8ca0a91ff5e02",
                    "sha256:9fb3fcee28a57a2dfecee72ed9e6cd097fb0c2acbed64277d8829e41da7c19c7",
                    "sha256:8817d578622bba11d51b89d51d05f4ef50f07a2dc626deb201ce85713acc3f92",
                    "sha256:be4ed5435cdac23309965c2aeaf27a398ff9209296d5eb567e3b291d5809399f",
                    "sha256:bfa746e6c0273b4553ed3339f1d889aeed3147ea3bd3b264f52ddfd9ead9d902",
                    "sha256:46d08055c513b9db80d0c558602b6ae73e2acaa455c09080c8e0e77ec7d6ca6f",
                    "sha256:e5d5bbe19de8ff1339d8244cbd8712f9d17d305686db36222786d6ee665f965c",
                    "sha256:996f4c5f4bad945a39c1c4c0d3f044121d646ad167d777a54e7bdbe435db60e0"
               ]
          },
          "Labels": {
               "build_version": "Linuxserver.io version:- 2.8.2-r3-ls123 Build-date:- 2025-02-25T20:36:45+00:00",
               "maintainer": "notdriz",
               "org.opencontainers.image.authors": "linuxserver.io",
               "org.opencontainers.image.created": "2025-02-25T20:36:45+00:00",
               "org.opencontainers.image.description": "[Smokeping](https://oss.oetiker.ch/smokeping/) keeps track of your network latency. For a full example of what this application is capable of visit [UCDavis](http://smokeping.ucdavis.edu/cgi-bin/smokeping.fcgi).",
               "org.opencontainers.image.documentation": "https://docs.linuxserver.io/images/docker-smokeping",
               "org.opencontainers.image.licenses": "GPL-3.0-only",
               "org.opencontainers.image.ref.name": "bf549a76f8bb1d9c573deca5071859a290a9bcb4",
               "org.opencontainers.image.revision": "bf549a76f8bb1d9c573deca5071859a290a9bcb4",
               "org.opencontainers.image.source": "https://github.com/linuxserver/docker-smokeping",
               "org.opencontainers.image.title": "Smokeping",
               "org.opencontainers.image.url": "https://github.com/linuxserver/docker-smokeping/packages",
               "org.opencontainers.image.vendor": "linuxserver.io",
               "org.opencontainers.image.version": "2.8.2-r3-ls123"
          },
          "Annotations": {},
          "ManifestType": "application/vnd.oci.image.manifest.v1+json",
          "User": "",
          "History": [
               {
                    "created": "2025-02-15T13:31:27.851956348Z",
                    "created_by": "COPY /root-out/ / # buildkit",
                    "comment": "buildkit.dockerfile.v0"
               },
               {
                    "created": "2025-02-15T13:31:28.025990556Z",
                    "created_by": "ARG BUILD_DATE=2025-02-15T13:30:29+00:00",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-15T13:31:28.025990556Z",
                    "created_by": "ARG VERSION=a0970cfe-ls21",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-15T13:31:28.025990556Z",
                    "created_by": "ARG MODS_VERSION=v3",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-15T13:31:28.025990556Z",
                    "created_by": "ARG PKG_INST_VERSION=v1",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-15T13:31:28.025990556Z",
                    "created_by": "ARG LSIOWN_VERSION=v1",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-15T13:31:28.025990556Z",
                    "created_by": "LABEL build_version=Linuxserver.io version:- a0970cfe-ls21 Build-date:- 2025-02-15T13:30:29+00:00",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-15T13:31:28.025990556Z",
                    "created_by": "LABEL maintainer=TheLamer",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-15T13:31:28.025990556Z",
                    "created_by": "ADD --chmod=755 https://raw.githubusercontent.com/linuxserver/docker-mods/mod-scripts/docker-mods.v3 /docker-mods # buildkit",
                    "comment": "buildkit.dockerfile.v0"
               },
               {
                    "created": "2025-02-15T13:31:28.232189122Z",
                    "created_by": "ADD --chmod=755 https://raw.githubusercontent.com/linuxserver/docker-mods/mod-scripts/package-install.v1 /etc/s6-overlay/s6-rc.d/init-mods-package-install/run # buildkit",
                    "comment": "buildkit.dockerfile.v0"
               },
               {
                    "created": "2025-02-15T13:31:28.407331202Z",
                    "created_by": "ADD --chmod=755 https://raw.githubusercontent.com/linuxserver/docker-mods/mod-scripts/lsiown.v1 /usr/bin/lsiown # buildkit",
                    "comment": "buildkit.dockerfile.v0"
               },
               {
                    "created": "2025-02-15T13:31:28.407331202Z",
                    "created_by": "ENV PS1=$(whoami)@$(hostname):$(pwd)\\$  HOME=/root TERM=xterm S6_CMD_WAIT_FOR_SERVICES_MAXTIME=0 S6_VERBOSITY=1 S6_STAGE2_HOOK=/docker-mods VIRTUAL_ENV=/lsiopy PATH=/lsiopy/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-15T13:31:29.903573906Z",
                    "created_by": "RUN |5 BUILD_DATE=2025-02-15T13:30:29+00:00 VERSION=a0970cfe-ls21 MODS_VERSION=v3 PKG_INST_VERSION=v1 LSIOWN_VERSION=v1 /bin/sh -c echo \"**** install runtime packages ****\" &&   apk add --no-cache     alpine-release     bash     ca-certificates     catatonit     coreutils     curl     findutils     jq     netcat-openbsd     procps-ng     shadow     tzdata &&   echo \"**** create abc user and make our folders ****\" &&   groupmod -g 1000 users &&   useradd -u 911 -U -d /config -s /bin/false abc &&   usermod -G users abc &&   mkdir -p     /app     /config     /defaults     /lsiopy &&   echo \"**** cleanup ****\" &&   rm -rf     /tmp/* # buildkit",
                    "comment": "buildkit.dockerfile.v0"
               },
               {
                    "created": "2025-02-15T13:31:30.062704552Z",
                    "created_by": "COPY root/ / # buildkit",
                    "comment": "buildkit.dockerfile.v0"
               },
               {
                    "created": "2025-02-15T13:31:30.062704552Z",
                    "created_by": "ENTRYPOINT [\"/init\"]",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-25T20:41:01.72687017Z",
                    "created_by": "ENV LSIO_FIRST_PARTY=true",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-25T20:41:01.72687017Z",
                    "created_by": "ARG BUILD_DATE=2025-02-25T20:36:45+00:00",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-25T20:41:01.72687017Z",
                    "created_by": "ARG VERSION=2.8.2-r3-ls123",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-25T20:41:01.72687017Z",
                    "created_by": "ARG SMOKEPING_VERSION=2.8.2-r3",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-25T20:41:01.72687017Z",
                    "created_by": "LABEL build_version=Linuxserver.io version:- 2.8.2-r3-ls123 Build-date:- 2025-02-25T20:36:45+00:00",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-25T20:41:01.72687017Z",
                    "created_by": "LABEL maintainer=notdriz",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-25T20:41:01.72687017Z",
                    "created_by": "RUN |3 BUILD_DATE=2025-02-25T20:36:45+00:00 VERSION=2.8.2-r3-ls123 SMOKEPING_VERSION=2.8.2-r3 /bin/sh -c echo \"**** install packages ****\" &&   if [ -z ${SMOKEPING_VERSION+x} ]; then     SMOKEPING_VERSION=$(curl -sL \"http://dl-cdn.alpinelinux.org/alpine/v3.20/main/x86_64/APKINDEX.tar.gz\" | tar -xz -C /tmp     && awk '/^P:smokeping$/,/V:/' /tmp/APKINDEX | sed -n 2p | sed 's/^V://');   fi &&   apk add --no-cache --virtual=build-dependencies     build-base     perl-app-cpanminus     perl-dev &&   apk add --no-cache     apache2     apache2-ctl     apache2-utils     apache-mod-fcgid     bc     bind-tools     font-noto-cjk     irtt     openssh-client     perl-authen-radius     perl-json-maybexs     perl-lwp-protocol-https     perl-path-tiny     smokeping==${SMOKEPING_VERSION}     ssmtp     sudo     tcptraceroute &&   echo \"**** Build perl TacacsPlus module ****\" &&   cpanm Authen::TacacsPlus &&   echo \"**** Build perl InfluxDB modules ****\" &&   cpanm InfluxDB::HTTP &&   cpanm Method::Signatures --force &&   cpanm Object::Result &&   cpanm InfluxDB::LineProtocol &&   echo \"**** give setuid access to traceroute & tcptraceroute ****\" &&   chmod a+s /usr/bin/traceroute &&   chmod a+s /usr/bin/tcptraceroute &&   echo \"**** fix path to cropper.js ****\" &&   sed -i 's#src=\"/cropper/#/src=\"cropper/#' /etc/smokeping/basepage.html &&   printf \"Linuxserver.io version: ${VERSION}\\nBuild-date: ${BUILD_DATE}\" > /build_version &&   echo \"**** Cleanup ****\" &&   apk del --purge     build-dependencies &&   rm -rf     /tmp/*     /root/.cpanm     /etc/apache2/httpd.conf # buildkit",
                    "comment": "buildkit.dockerfile.v0"
               },
               {
                    "created": "2025-02-25T20:41:01.936163446Z",
                    "created_by": "COPY root/ / # buildkit",
                    "comment": "buildkit.dockerfile.v0"
               },
               {
                    "created": "2025-02-25T20:41:01.936163446Z",
                    "created_by": "EXPOSE map[80/tcp:{}]",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               },
               {
                    "created": "2025-02-25T20:41:01.936163446Z",
                    "created_by": "VOLUME [/config /data]",
                    "comment": "buildkit.dockerfile.v0",
                    "empty_layer": true
               }
          ],
          "NamesHistory": [
               "lscr.io/linuxserver/smokeping:latest",
               "localhost/smokeping:deployed"
          ]
     }
]
