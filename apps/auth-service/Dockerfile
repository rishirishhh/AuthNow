# This file is generated by Nx.
#
# Build the docker image with `npx nx docker-build @auth-now/auth-service`.
# Tip: Modify "docker-build" options in project.json to change docker build args.
#
# Run the container with `docker run -p 3000:3000 -t auth-now-auth-service`.
FROM docker.io/node:lts-alpine

ENV HOST=0.0.0.0
ENV PORT=3000

WORKDIR /app

RUN addgroup --system auth-now-auth-service && \
          adduser --system -G auth-now-auth-service auth-now-auth-service

COPY apps/auth-service/dist auth-now-auth-service/
COPY apps/auth-service/package.json auth-now-auth-service/
RUN chown -R auth-now-auth-service:auth-now-auth-service .

# You can remove this install step if you build with `--bundle` option.
# The bundled output will include external dependencies.
RUN npm --prefix auth-now-auth-service --omit=dev -f install

CMD [ "node", "auth-now-auth-service" ]
