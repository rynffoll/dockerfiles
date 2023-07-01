VERSION = 8.8.20

all: docker

download:
	mkdir -p build/
	wget -P build/ -c https://www.gridgain.com/media/gridgain-community-$(VERSION).zip
	unzip -n build/gridgain-community-$(VERSION).zip -d build/
	mv -n build/gridgain-community-$(VERSION) build/gridgain-community
	wget -P build/gridgain-community -c https://raw.githubusercontent.com/gridgain/gridgain/$(VERSION)/modules/kubernetes/config/run.sh
	chmod +x build/gridgain-community/run.sh

clean:
	rm -r build/

docker:
	docker build -t gridgain-community:$(VERSION) --build-arg VERSION=$(VERSION) .
