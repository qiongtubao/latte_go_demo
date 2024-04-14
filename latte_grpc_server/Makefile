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

LATTE_GRPC_SERVER_DEP :=
latte_grpc_server: ${LATTE_GRPC_SERVER_DEP}
	CGO_ENABLED=$(BUILD_CGO_ENABLED) go build $(BUILD_FLAGS) -gcflags '$(GCFLAGS)' -ldflags '$(LDFLAGS)' -tags "$(BUILD_TAGS)" -o $(BUILD_BIN_PATH)/latte_grpc_server cmd/latte_grpc_server/main.go

latte_grpc_client: ${LATTE_GRPC_SERVER_DEP}
	CGO_ENABLED=$(BUILD_CGO_ENABLED) go build $(BUILD_FLAGS) -gcflags '$(GCFLAGS)' -ldflags '$(LDFLAGS)' -tags "$(BUILD_TAGS)" -o $(BUILD_BIN_PATH)/latte_grpc_client cmd/latte_grpc_client/main.go

all: latte_grpc_server latte_grpc_client

