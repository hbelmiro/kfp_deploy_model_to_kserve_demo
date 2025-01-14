# Using Data Science Pipelines to deploy a model to KServe in OpenShift AI

In a cluster with the following operators installed:

* Red Hat OpenShift AI
  * Create a `DataScienceCluster` instance
* Red Hat Authorino
* Red Hat OpenShift Service Mesh
* Red Hat OpenShift Serverless

1. Set a namespace and deploy the manifests:

    ```shell
    export NAMESPACE=<your-namespace>
    kustomize build manifests | envsubst | oc apply -f -
    ```

2. Install the required Python dependencies

    ```shell
    pip install -r requirements.txt
    ```
      
3. Compile the pipeline

    ```shell
    kfp dsl compile --py pipeline.py --output pipeline.yaml
    ```

4. Deploy the compiled pipeline (`pipeline.yaml`) in the Red Hat OpenShift AI console
5. Run the pipeline in the Red Hat OpenShift AI console