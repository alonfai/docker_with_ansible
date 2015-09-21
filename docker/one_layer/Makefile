registry := devopsquality/ansible_docker
tag := $(registry)/wordpress_one_layer:latest

wordpress_one_layer: Dockerfile
	rm -rf ansible_playbooks && cp -a ../../ansible/playbooks ansible_playbooks
	docker build -t $(tag) .

push:
	docker push $(tag)

clean:
	rm -rf ansible_playbooks
	docker rmi $(tag)
