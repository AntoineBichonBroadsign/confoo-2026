gnerate container without dockerfile

standardized

language agnostic : if buildpack work, same process

paketo :one implementation of buildpacks

paketo-buildpacks/samples

can install libraries with apt on the image.

oci images in result.

adoption : 
- what langauge support ?
- what builder to use ? (base image + buildpack)
- need for extra os package ?
- ca certs ?


ci/cd : 
- cli `pack`
- circleci supopoirted
- can reference the builder image as image to run ci
