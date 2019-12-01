VERSION = 8.7.7

all: build

build:
	docker build -t gridgain-community:$(VERSION) --build-arg VERSION=$(VERSION) .
