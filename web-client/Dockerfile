# Stage 1: Git clone the WebGL client files
FROM alpine:latest AS fetcher

RUN apk add --no-cache git ca-certificates

# Clone the web client directly from official repository
RUN git clone https://github.com/nzp-team/nzp-team.github.io.git /app

# Stage 2: Serve with Nginx
FROM nginx:alpine

# Copy web files from stage 1 into Nginx HTML directory
COPY --from=fetcher /app /usr/share/nginx/html

# Automatically set correct permissions inside the container
RUN chmod -R 755 /usr/share/nginx/html && \
    chown -R nginx:nginx /usr/share/nginx/html

EXPOSE 80
