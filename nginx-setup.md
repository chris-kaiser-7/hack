export GW_API_VERSION=main
export ENABLE_EXPERIMENTAL=true
export TAG=$(whoami)

make create-kind-cluster install-ngf-local-build build-test-runner-image run-conformance-tests

# make create-kind-cluster
# make install-ngf-local-build
# make build-test-runner-image
# make run-conformance-tests

# make build-images load-images 
# make update-go-modules
