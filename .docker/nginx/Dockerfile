FROM nginx:1.21-alpine
# IMAGEN OFICIAL DE NGINX ALPINE 

# REEMPLAZO ARCHIVOS DE CONFIGURACION
COPY nginx.conf  /etc/nginx/
COPY templates /etc/nginx/templates/
RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf

# PUERTOS DE SALIDA
EXPOSE 80
EXPOSE 443
