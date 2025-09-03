NAME = inception

all: up

up:
	docker-compose -f srcs/docker-compose.yml up -d --build

down:
	docker-compose -f srcs/docker-compose.yml down

build:
	docker-compose -f srcs/docker-compose.yml build

logs:
	docker-compose -f srcs/docker-compose.yml logs -f

ps:
	docker-compose -f srcs/docker-compose.yml ps

clean: down
	docker system prune -af --volumes

re: clean all
