EDITOR=vim

all: build

build:
	docker build -t dezota/dremio-oss-with-ext-thin:24.1.0-2 .

run:
	docker-compose up -d

login:
	docker login -u bkholman

push: 
	docker push dezota/dremio-oss-with-ext-thin:24.1.0-2
	
