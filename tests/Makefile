DOCKER_COMPOSE=docker-compose

UNAME_S := $(shell uname -s)
ifeq ($(UNAME_S), Darwin)
	OPEN_CMD        ?= open
	DOCKER_HOST_IP  ?= $(shell echo $(DOCKER_HOST) | sed 's/tcp:\/\///' | sed 's/:[0-9.]*//')
else
	OPEN_CMD        ?= xdg-open
	DOCKER_HOST_IP  ?= 127.0.0.1
endif

open:	 ##@docker open application web service in browser
	$(OPEN_CMD) http://$(DOCKER_HOST_IP):$(shell $(DOCKER_COMPOSE) port nginx 80 | sed 's/[0-9.]*://')

open-db:	 ##@docker open application web service in browser
	$(OPEN_CMD) mysql://admin:secretadmin@$(DOCKER_HOST_IP):$(shell $(DOCKER_COMPOSE) port mariadb 3306 | sed 's/[0-9.]*://')

bash:	##@docker open application shell in container
	$(DOCKER_COMPOSE) run --rm phpfpm bash