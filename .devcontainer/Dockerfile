# [Choice] .NET version: 5.0, 3.1, 2.1
ARG VARIANT="6.0"
FROM mcr.microsoft.com/dotnet/sdk:${VARIANT}

ARG USER=dev
ARG UID=19000
ARG GID=${UID}

RUN groupadd -g ${GID} -r ${USER} &&\
    useradd -u ${UID} -r -g ${USER} -m -s $(which bash) ${USER}

# [Choice] Node.js version: none, lts/*, 16, 14, 12, 10
ARG NODE_VERSION="none"
RUN if [ "${NODE_VERSION}" != "none" ]; then su ${USER} -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# RUN su ${USER} -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1

USER ${USER}
ENV PATH=/home/${USER}/.dotnet/tools:$PATH