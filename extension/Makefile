# Use a single shell for every target recipe task (one line) - allows simpler chaining
.ONESHELL: true
# Silence maketask execution lines
MAKEFLAGS += --silent

export VERSION

node_env ?= production
target ?= chrome

prepare:
	mkdir -p dist

install-dependencies:
	npm install --no-save && make prepare

build:
	export TARGET=$(target) NODE_ENV=$(node_env) && echo "RUN BUILD for $$TARGET and $$NODE_ENV"

package:
	make prepare && echo "PACKAGE"

publish-live:
	make package && echo "PUBLISH LIVE"

publish-preview:
	make package && echo "PUBLISH PREVIEW"

bump:
	npm version $(step)

run:
	export NODE_ENV=development TARGET=$(target) && echo "RUN START for $$TARGET and $$NODE_ENV"

test:
	export NODE_ENV=test && echo "RUN TEST for $$NODE_ENV"

ci-test:
	export NODE_ENV=test && echo "RUN TEST for $$NODE_ENV"

test-pipeline:
	export NODE_ENV=test && echo "RUN TEST PIPELINE for $$NODE_ENV"

ci-test-pipeline:
	export NODE_ENV=test && echo "RUN TEST PIPELINE for $$NODE_ENV"

lint:
	echo "RUN LINT"

ci-lint:
	echo "RUN LINT"

current-version:
	node -p 'require("./package.json").version'
