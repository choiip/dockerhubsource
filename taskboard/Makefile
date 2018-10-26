include ../Makefile.mk

DOCKER_BUILD_ARGS=--rm
REGISTRY_HOST=docker.io
USERNAME=choiip
NAME=taskboard
CONTAINERNAME=$(USERNAME)-$(NAME)

start:
	@docker start $(CONTAINERNAME) || docker run --name $(CONTAINERNAME) -p 8080:80 -d $(USERNAME)/$(NAME)

stop:
	@docker stop $(CONTAINERNAME)
