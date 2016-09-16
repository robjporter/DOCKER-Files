FROM scratch
ADD ca-certificates.crt /etc/ssl/certs/
ADD main /
CMD ["/main"]

# Document that the service listens on port 8080.
EXPOSE 8080 443
