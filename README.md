# Cloud Builders

[![Apache-2.0 License](https://img.shields.io/github/license/bluk/gcp-cloud-builders.svg)](https://github.com/bluk/gcp-cloud-builders/blob/master/LICENSE)

Contains unsupported [Google Cloud Build](https://cloud.google.com/cloud-build/)
image definitions.

## Getting Started

1. To build one of the images, clone this repository and change to the directory
   of the image you want.

   ```
   git clone --recurse-submodules git@github.com:bluk/gcp-cloud-builders.git
   # or
   git clone --recursive git@github.com:bluk/gcp-cloud-builders.git

   cd gcp-cloud-builders
   cd swift-build-tools
   ```

2. Submit a one-time build job to create the images in your Google Cloud
   project's container registry.

    ```
    gcloud builds submit . --config=cloudbuild.yaml
    ```

   You may have to install the beta components to get the `gcloud builds`
   command.

    ```
    gcloud components install beta
    ```

3. Then in *your* project's `cloudbuild.yaml`, use the built image like:

    ```
    steps:
      - name: 'gcr.io/$PROJECT_ID/swift-build-tools'
        args:
          - 'swift'
          - 'build'
    ```

## Related Links

* [Google Cloud Build](https://cloud.google.com/cloud-build/)
* [Supported Cloud Builders](https://github.com/GoogleCloudPlatform/cloud-builders)
* [Cloud Builders Community](https://github.com/GoogleCloudPlatform/cloud-builders-community)

## License

[Apache-2.0 License](https://github.com/bluk/gcp-cloud-builders/blob/master/LICENSE)
