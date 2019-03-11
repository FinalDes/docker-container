FROM ubuntu:latest as setup
RUN groupadd --gid 1000 meteor \
  && useradd --uid 1000 --gid meteor --shell /bin/bash --create-home meteor
RUN apt-get update && apt-get install curl -y
USER meteor
WORKDIR /home/meteor
RUN curl "https://install.meteor.com/" | sh
# RUN .meteor/meteor update --release 1.4.4.6

From ubuntu:latest as meteor
RUN groupadd --gid 1000 meteor \
  && useradd --uid 1000 --gid meteor --shell /bin/bash --create-home meteor
WORKDIR /home/meteor
USER meteor
COPY --from=setup /home/meteor/. .
ENTRYPOINT ".meteor/meteor"

