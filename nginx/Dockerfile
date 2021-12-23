FROM nginx:1.19.7-alpine

# Add bash for boot cmd
RUN apk add bash

# Add nginx.conf to container
COPY  nginx.conf /etc/nginx/nginx.conf
COPY  start.sh /app/start.sh

# set workdir
WORKDIR /app

# permissions and nginx user for tightened security
RUN chmod -R 755 /app && chmod -R 755 /app && \
        chmod -R 755 /var/cache/nginx && \
        chmod -R 755 /var/log/nginx && \
        chmod -R 755 /var/log/nginx; \
        chmod -R 755 /etc/nginx/conf.d
RUN touch /var/run/nginx.pid && chown -R 755 /var/run/nginx.pid

# # Uncomment to keep the nginx logs inside the container - Leave commented for logging to stdout and stderr
# RUN mkdir -p /var/log/nginx
# RUN unlink /var/log/nginx/access.log \
#     && unlink /var/log/nginx/error.log \
#     && touch /var/log/nginx/access.log \
#     && touch /var/log/nginx/error.log \
#     && chmod nginx /var/log/nginx/*log \
#     && chmod 644 /var/log/nginx/*log

USER nginx

CMD ["nginx", "-g", "'daemon off;'"]
