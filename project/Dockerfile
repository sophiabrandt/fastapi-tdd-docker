###############
# BUILD IMAGE #
###############
FROM python:3.8.3-slim-buster AS build

# virtualenv
ENV VIRTUAL_ENV=/opt/venv
RUN python3 -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# install system dependencies
RUN apt-get update \
  && apt-get -y install gcc \
  && apt-get clean

# add and install requirements
RUN pip install --upgrade pip
COPY ./requirements.txt .
COPY ./requirements-dev.txt .
RUN pip install --no-cache-dir -r requirements-dev.txt

#################
# RUNTIME IMAGE #
#################
FROM python:3.8.3-slim-buster AS runtime

# create user
ARG USER_ID=1000
ENV USER_ID $USER_ID
ARG GROUP_ID=1000
ENV GROUP_ID $GROUP_ID

# add non-root user and give permissions to workdir
RUN groupadd --gid $GROUP_ID user && \
          adduser user --ingroup user --gecos '' --disabled-password --uid $USER_ID && \
          mkdir -p /usr/src/app && \
          chown -R user:user /usr/src/app

# install system dependencies
RUN apt-get update \
  && apt-get -y install netcat-openbsd postgresql \
  && apt-get clean

# copy from build image
COPY --chown=user:user --from=build /opt/venv /opt/venv

# set working directory
WORKDIR /usr/src/app

# switch to non-root user
USER user

# disables lag in stdout/stderr output
ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1
# Path
ENV PATH="/opt/venv/bin:$PATH"

# run entrypoint.sh
ENTRYPOINT ["/usr/src/app/entrypoint.sh"]
