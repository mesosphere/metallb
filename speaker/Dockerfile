FROM quay.io/metallb/speaker:v0.12.1 AS source

FROM alpine:latest

COPY --from=source frr-reloader.sh /frr-reloader.sh
COPY --from=source frr-metrics /frr-metrics
COPY --from=source speaker /speaker

# When running as non root and building in an environment that `umask` masks out
# '+x' for others, it won't be possible to execute. Make sure all can execute,
# just in case
RUN chmod a+x /speaker /frr-reloader.sh

ENTRYPOINT ["/speaker"]
