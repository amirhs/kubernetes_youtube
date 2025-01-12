# Fluentd Dockerfile
FROM fluent/fluentd:v1.16-1

WORKDIR /fluentd

# Create necessary directories
RUN mkdir -p /fluentd/logs && \
    chown -R fluent /fluentd/logs

# Switch to fluent user
USER fluent 

# Expose Fluentd default port (if needed)
EXPOSE 24224

# Run Fluentd with configuration file from the Kubernetes ConfigMap
CMD ["fluentd", "-c", "/fluentd/etc/fluentd.conf", "-v"]