FROM nginx:1.19.8


COPY default.conf /etc/nginx/conf.d/default.conf
COPY html/ /var/www/html
COPY nginx.conf /etc/nginx/nginx.conf


# COPY ssl/nginx-selfsigned.crt /app/ssl/certs/nginx-selfsigned.crt
# COPY ssl/private/nginx-selfsigned.key /app/ssl/private/nginx-selfsigned.key


# WORKDIR /app
# RUN chown -R nginx:nginx /app && chmod -R 755 /app && \
#         chown -R nginx:nginx /var/cache/nginx && \
#         chown -R nginx:nginx /app/ssl/certs/nginx-selfsigned.crt && \
#         chown -R nginx:nginx /app/ssl/private/nginx-selfsigned.key && \
#         chown -R nginx:nginx /var/log/nginx && \
#         chown -R nginx:nginx /etc/nginx/conf.d && \
#         touch /var/run/nginx.pid && \
#         chown -R nginx:nginx /var/run/nginx.pid


# USER nginx