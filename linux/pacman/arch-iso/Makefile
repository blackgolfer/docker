DOCKER_USER:=blackgolfer
DOCKER_ORGANIZATION:=blackgolfer
DOCKER_IMAGE:=archlinux-iso

docker-image: 
	docker build -t $(DOCKER_ORGANIZATION)/$(DOCKER_IMAGE) .

docker-push: docker-image
	docker login -u $(DOCKER_USER)
	docker push $(DOCKER_ORGANIZATION)/$(DOCKER_IMAGE)

.PHONY: rootfs  docker-push
