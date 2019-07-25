ARG NODE_VERSION=12.6.0
FROM node:${NODE_VERSION}-alpine

ARG ADD_APK_PACKAGES=""
RUN apk add --no-cache ${ADD_APK_PACKAGES} && \
    rm -rf /var/cache/* /tmp/* /var/log/* ~/.cache

ARG UNAME="mb"
ARG HOST_UID=1000
ARG SHELL="/bin/sh"
RUN adduser -D ${UNAME} -u ${HOST_UID} -s ${SHELL}

USER ${UNAME}
WORKDIR /home/${UNAME}

ARG ADD_NPM_PACKAGES="mountebank@2.1.0"
RUN npm install ${ADD_NPM_PACKAGES} --production --no-save \
    && npm cache clean --force \
    && rm -rf /tmp/npm*

COPY --chown=mb:mb testapi testapi

EXPOSE 2525
EXPOSE 8273

ENTRYPOINT ["node_modules/.bin/mb"]
CMD ["--allowInjection", "--configfile", "testapi/apis.ejs"]
