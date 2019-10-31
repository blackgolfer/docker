DOCKER_USER:=blackgolfer
DOCKER_ORGANIZATION:=blackgolfer
DOCKER_IMAGE:=manjaro-iso
ISO-PROFILE:=xfce

iso-profiles: git clone https://gitlab.manjaro.org/profiles-and-settings/iso-profiles.git iso-profiles

docker-image: iso-profiles
	docker build -t $(DOCKER_ORGANIZATION)/$(DOCKER_IMAGE) .


docker-push: docker-image
	docker login -u $(DOCKER_USER)
	docker push $(DOCKER_ORGANIZATION)/$(DOCKER_IMAGE)

.PHONY: iso-profiles docker-image docker-push
