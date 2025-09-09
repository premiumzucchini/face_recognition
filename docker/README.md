# Docker Builds

If you've never used Docker before, check out the [getting started guide.](https://docs.docker.com/get-started/)

Up-to-date prebuilt images can be found [on Docker hub.](https://hub.docker.com/repository/docker/sanjeevk/face_recognition)

## CPU Images

-	[`cpu-latest`, `cpu`, `cpu-0.1`, `latest`](cpu/Dockerfile)
-	[`cpu-jupyter-kubeflow-latest`, `cpu-jupyter-kubeflow`, `cpu-jupyter-kubeflow-0.1`](cpu-jupyter-kubeflow/Dockerfile)

### GPU Images
-	[`gpu-latest`, `gpu`, `gpu-0.1`](gpu/Dockerfile)
-	[`gpu-jupyter-kubeflow-latest`, `gpu-jupyter-kubeflow`, `gpu-jupyter-kubeflow-0.1`](gpu-jupyter-kubeflow/Dockerfile)

The CPU images should run out of the box without any driver prerequisites.

## GPU Images

### Prerequisites

To use the GPU images, you need to have:
- [The Nvidia drivers](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#nvidia-drivers)
- [The Nvidia-docker container runtime](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#setting-up-nvidia-container-toolkit)
- [Docker configured to use the Nvidia container runtime](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/user-guide.html#daemon-configuration-file)

Once you have those installed, you should be ready to start running the GPU instances.

### Testing GPUs

To make sure your GPU instance is setup correctly, run the following in a container:

```python3
import dlib
print(dlib.cuda.get_num_devices())
```

## Jupyter Images

The Jupyter images are built to be deployed on [Kubeflow](https://www.kubeflow.org/). However, if you just want to run a normal Jupyter instance, they're a great template to build your own.

## Example Dockerfile

Here's an example Dockerfile using the prebuilt images:

```Dockerfile
FROM sanjeevk/face_recognition:gpu

COPY requirements.txt requirements.txt

RUN pip3 install -r ./requirements.txt

COPY my_app /my_app

CMD [ "python3", "/my_app/my_app.py" ]
```

## About the Maintainer

This project is actively maintained by Sanjeev Preetam K.

Sanjeev is a Data Analyst with over 3 years of professional experience, specializing in architecting end-to-end data solutions, developing advanced machine learning models, and orchestrating scalable analytics workflows. He has a proven track record in deploying AI-driven systems using Python, PyTorch, and cloud technologies (AWS, GCP) to derive meaningful insights and accelerate business intelligence. Sanjeev is adept at integrating data engineering, model optimization, and statistical inference to solve complex business challenges.

For inquiries or contributions, please connect:
- Email: karrisanjeevpreetam@gmail.com
- GitHub: [Sanjeev Preetam K](https://github.com/sanjeevk)
- LinkedIn: [Sanjeev Preetam K](https://www.linkedin.com/in/sanjeevk)