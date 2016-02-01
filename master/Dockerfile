FROM armhfbuild/golang:1.5.3

RUN GO15VENDOREXPERIMENT=1 go get github.com/prometheus/prometheus/cmd/...
RUN mkdir -p /prometheus \
  /etc/prometheus \
  /etc/prometheus/consoles \
  /etc/prometheus/console_libraries

RUN cp /go/bin/prometheus /bin/
COPY prometheus.yml /etc/prometheus/

EXPOSE 9090
VOLUME ["/prometheus"]
WORKDIR /prometheus
ENTRYPOINT ["/bin/prometheus"]
CMD ["-config.file=/etc/prometheus/prometheus.yml", \
  "-storage.local.path=/prometheus"]
