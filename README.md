# Sample project: cd_docker_platform_ship

This sample project demonstrates how to automate deployments of a Docker image to a Container orchestration platform like Kubernetes, GKE, Amazon ECS, etc.

You can find a tutorial that explains how to run this sample at http://docs.shippable.com/deploy/continuous-delivery-single-container-docker-application/

## Quickstart guide to running this tutorials

You can do a quick test run of this project by following the instructions below. Please note that these instructions will deploy our sample application to a container orchestration service of your choice.

* Clone this repository to your account

* The sample assumes you have a cluster where the application can be deployed. Create an integration for the cloud where your cluster is located:
    * GKE: [gCloudKey](http://docs.shippable.com/platform/integration/gcloudKey/)
    * Kubernetes: [Kubernetes](http://docs.shippable.com/platform/integration/kubernetes/)
    * Amazon ECS: [AWS IAM](http://docs.shippable.com/platform/integration/aws-iam/) or [AWS keys](http://docs.shippable.com/platform/integration/aws-keys/)

* In **shippable.yml**, replace values for `sourceName` and `region` in the `cluster` resource.

```
- name: cd_docker_platform_cluster
  type: cluster
  integration: "drship_gcp"
  versionTemplate:
    sourceName : "cd_docker_platform_ship_cluster"  # replace with your cluster name
    region: "us-central-1f"         # replace with your region
    namespace: "shippable"          # replace with your namespace

```

* Commit your changes to **shippable.yml**.

* [Sign in to Shippable](https://app.shippable.com)

* Follow instructions to [Add your assembly line to Shippable](http://docs.shippable.com/platform/tutorial/workflow/add-assembly-line/)

* In your Single Pane of Glass view, right click on the manifest job **cd_docker_platform_manifest** and click on the **Play** icon to run the job. This will create your service definition and automatically trigger the deploy job, which deploys your application to your cluster.

## Related tutorials

* If you want to automate how the Docker image is pushed to Docker Hub, please read our tutorial [Build and Push an image to Docker Hub](http://docs.shippable.com/ci/tutorial/build-push-image-to-docker-hub/). Please note that you will need to make the following changes to this sample once you have that workflow set up:
    * In the **cd_docker_platform_manifest** job, replace the `IN` image resource **cd_docker_platform_image** with **node_app_img_dh**, which defined in the "Build and Push an image to Docker Hub" tutorial to create a continuous workflow from that tutorial to this.
    * Remove the `image` resource **cd_docker_platform_image** from this sample

* Advanced scenarios such as scaling number of instances, customizing container options, etc are explained in the docs:
    - [Multi-container deployments](http://docs.shippable.com/deploy/continuous-delivery-multi-container-docker-application/)
    - [Multi-stage deployments](http://docs.shippable.com/deploy/multi-stage-deployments)
    - [Gated deployments](http://docs.shippable.com/deploy/gated-deployments)
    - [Specifying deployment methods](http://docs.shippable.com/deploy/deployment-methods-overview)
    - [Customizing container options](http://docs.shippable.com/deploy/tutorial/customizing-container-options)
    - [Setting environment variables inside deployed container](http://docs.shippable.com/deploy/tutorial/set-environment-deployed-container)
    - [Scaling service instances](http://docs.shippable.com/deploy/tutorial/scaling-services)
    - [Specifying the version to deploy](http://docs.shippable.com/deploy/deploying-specific-version)
    - [Rolling back deployments](http://docs.shippable.com/deploy/rollback)
    - [Sending notifications upon deployments](http://docs.shippable.com/deploy/deployment-notifications)
    - [Customizing deployed service names](http://docs.shippable.com/deploy/customize-service-names)
    - [Pausing deployments](http://docs.shippable.com/deploy/pause-deployments)
    - [Deleting a deployed service](http://docs.shippable.com/deploy/deleting-a-service)

## Shippable overview

If you're new to Shippable and need an overview of how everything works, please start here:

* [What is Shippable](http://docs.shippable.com)
* [Platform overview](http://docs.shippable.com/platform/overview)
* [Workflow configuration](http://docs.shippable.com/platform/workflow/config/)
* [Platform tutorials](http://docs.shippable.com/platform/tutorials/)
* [Deployment tutorials](http://docs.shippable.com/deploy/tutorials/)
