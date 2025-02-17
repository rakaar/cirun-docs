# Cirun.yml Examples

## GCP

```yaml
# Self-Hosted Github Action Runners on GCP via Cirun.io
# Reference: https://docs.cirun.io/reference/yaml.html
runners:
  - name: gpu-runner
    # Cloud Provider: GCP
    cloud: gcp
    # Cheapest GPU on GCP
    gpu: nvidia-tesla-t4
    # Cheapest VM on GCP, with GPU attachable
    instance_type: n1-standard-1
    # Ubuntu-20.4, can be seen from "gcloud compute images list"
    machine_image: ubuntu-minimal-2004-lts
    # preemptible instances seems quite less reliable.
    preemptible: false
    # Path of the relevant workflow file
    workflow: .github/workflows/build-gpu.yml
    # Number of runners to provision on every trigger on Actions job
    # 3 because testing on Python 3.7, 3.8, 3.9
    # See .github/workflows/build-gpu.yml
    count: 3
    # Adding the GPU label, this matches the runs-on param from .github/workflows/build-gpu.yml
    # So that this runner is selected for running .github/workflows/build-gpu.yml
    labels:
      - gpu
```

## DigitalOcean

```yaml
# Self-Hosted Github Action Runners on GCP via Cirun.io
# Reference: https://docs.cirun.io/reference/yaml.html
runners:
  - name: do-runner
    # Cloud Provider: DigitalOcean
    cloud: digitalocean
    # Cheapest VM on DigitalOcean
    instance_type: s-1vcpu-1gb
    # Ubuntu-20.4  image"
    machine_image: ubuntu-20-04-x64
    # Path of the relevant workflow file
    workflow: .github/workflows/test.yml
    # Number of runners to provision on every trigger on Actions job
    # 3 because testing on Python 3.7, 3.8
    # See .github/workflows/build-gpu.yml
    count: 2
```

## AWS

```yaml
# Self-Hosted Github Action Runners on GCP via Cirun.io
# Reference: https://docs.cirun.io/reference/yaml.html
runners:
  - name: gpu-runner
    # Cloud Provider: AWS
    cloud: aws
    # Cheapest VM on AWS
    instance_type: t3.nano
    # Ubuntu-20.4, ami image"
    machine_image: ami-06fd8a495a537da8b
    # preemptible instances seems quite less reliable.
    preemptible: false
    # Path of the relevant workflow file
    workflow: .github/workflows/test.yml
    # Number of runners to provision on every trigger on Actions job
    # 3 because testing on Python 3.7, 3.8
    # See .github/workflows/build-gpu.yml
    count: 2
```
