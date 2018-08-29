FROM envoyproxy/envoy:latest

COPY envoy.yaml /etc/envoy.yaml

EXPOSE 8080
EXPOSE 8081

CMD ["/usr/local/bin/envoy", "-c", "/etc/envoy.yaml", "--log-level", "debug"]
