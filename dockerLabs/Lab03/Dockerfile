FROM alpine as builder
LABEL maintainer="maxim"
RUN echo "Welcome to DockerLabs!" > /opt/index.html

#if we want to create this index file, we can't just do it in the nginx continer, so we need a linux distro to do this first. 
#including this distro in the final build is not needed, and would make a massive image, so we set it as the builder
#then we copy the file over from the builder to the next stage to keep whatever we did in that image, without retaining all the layers / things we don't need. !!!

FROM nginx:alpine
LABEL maintainer="maxim"
COPY --from=builder /opt/index.html /usr/share/nginx/hmtl/
ENTRYPOINT ["nginx","-g","daemon off;"]