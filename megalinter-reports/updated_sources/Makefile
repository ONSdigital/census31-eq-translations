build:
	poetry install

lint:
	poetry run flake8 --max-complexity 10 --count
	poetry run pylint eq_translations ./tests
	poetry run black --check eq_translations tests

format:
	poetry run black .

test:
	poetry run pytest --cov-config=.coveragerc --cov --cov-report html tests

.PHONY: megalint megalint-apply clean-megalint
megalint:
	docker run --platform linux/amd64 --rm \
		-v /var/run/docker.sock:/var/run/docker.sock:rw \
		-v $(shell pwd):/tmp/lint:rw \
		ghcr.io/oxsecurity/megalinter:v9.6.0

megalint-apply:
	docker run --platform linux/amd64 --rm \
		-v /var/run/docker.sock:/var/run/docker.sock:rw \
		-v $(shell pwd):/tmp/lint:rw \
		-e APPLY_FIXES=all \
		ghcr.io/oxsecurity/megalinter:v9.6.0

clean-megalint:
	rm -rf megalinter-reports
