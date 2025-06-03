FROM itzg/minecraft-server

COPY ./paper-global.yml /config/paper-global.yml
COPY ./world /data/world
COPY ./ops.json /data/ops.json
COPY ./plugins /data/plugins

RUN chown -R 1000:1000 /data
RUN chown -R 1000:1000 /data/ops.json
RUN chown -R 1000:1000 /data/plugins
RUN chown -R 1000:1000 /data/world