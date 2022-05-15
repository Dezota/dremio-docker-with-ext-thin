EDITOR=vim

all: build

build:
	docker build -t dezota/dremio-oss-with-ext-thin:21.1.1-1 .

run:
	docker-compose up -d

login:
	docker login -u bkholman

push: 
	docker push dezota/dremio-oss-with-ext-thin:21.1.1-1
	
