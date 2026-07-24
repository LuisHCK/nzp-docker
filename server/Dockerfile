FROM debian:bookworm-slim

# Install standard dependencies required by FTEQW
RUN apt-get update && apt-get install -y libsdl2-2.0-0 && rm -rf /var/lib/apt/lists/*

# Run as non-root user
RUN useradd -ms /bin/bash nzp
USER nzp
WORKDIR /home/nzp/server

COPY --chown=nzp:nzp . .
RUN chmod +x nzportable64-sdl

# Expose WebSockets TCP Port
EXPOSE 27500/tcp

# Launch game server on map 'ndu' (Nacht der Untoten)
ENTRYPOINT ["./nzportable64", "-dedicated", "+map", "ndu"]

# Set WebSockets protocol mode and port
CMD ["+com_protocolname", "NZP-REBOOT-WEB", "+sv_public", "1", "+sv_port_tcp", "27500"]
