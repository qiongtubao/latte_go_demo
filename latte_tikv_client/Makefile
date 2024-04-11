ROOT_PATH := $(shell pwd)
BUILD_BIN_PATH := $(ROOT_PATH)/bin
BUILD_FLAGS ?=
BUILD_TAGS ?=
BUILD_CGO_ENABLED := 0
PD_EDITION ?= Community
# Ensure PD_EDITION is set to Community or Enterprise before running build process.
ifneq "$(PD_EDITION)" "Community"
ifneq "$(PD_EDITION)" "Enterprise"
  $(error Please set the correct environment variable PD_EDITION before running `make`)
endif
endif

LATTE_TIKV_CLIENT_DEP :=
latte_tikv_client: ${LATTE_TIKV_CLIENT_DEP}
	CGO_ENABLED=$(BUILD_CGO_ENABLED) go build $(BUILD_FLAGS) -gcflags '$(GCFLAGS)' -ldflags '$(LDFLAGS)' -tags "$(BUILD_TAGS)" -o $(BUILD_BIN_PATH)/latte_tikv_client cmd/latte_tikv_client/main.go
