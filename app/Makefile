.PHONY : start deploy check test

start:
	yarn start

deploy:
	rm -f /etc/nginx/sites-enabled/default
	rm -f /etc/service/nginx/down
	yarn build
	/sbin/my_init

check:
	prettier --check src/**/*.js && echo OK
	eslint src/**/*.js && echo OK

test:
	yarn test --coverage
