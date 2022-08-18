---
layout: page
title: Machine Learning on Kubernetes - Подготовка окружения
description: Machine Learning on Kubernetes - Подготовка окружения
keywords: Machine Learning on Kubernetes - Подготовка окружения
permalink: /study/books/machine-learning-on-kubernetes/environment/
---

# Подготовка окружения

<br/>

### Technical requirements

<br/>

• A central processing unit (CPU) with at least four cores; eight are recommended
• Memory of at least 16 gigabytes (GB); 32 GB is recommended
• Disk with available space of at least 60 GB

<br/>

### Поднимаем

```
$ export \
    PROFILE=marley-minikube \
    CPUS=8 \
    MEMORY=30G \
    HDD=80G \
    DRIVER=docker \
    KUBERNETES_VERSION=v1.24.3
```

<br/>

```
$ {
    minikube --profile ${PROFILE} config set memory ${MEMORY}
    minikube --profile ${PROFILE} config set cpus ${CPUS}
    minikube --profile ${PROFILE} config set disk-size ${HDD}

    minikube --profile ${PROFILE} config set driver ${DRIVER}

    minikube --profile ${PROFILE} config set kubernetes-version ${KUBERNETES_VERSION}
    minikube start --profile ${PROFILE} --embed-certs

    // Enable ingress
    minikube addons --profile ${PROFILE} enable ingress

    // Enable registry
    // minikube addons --profile ${PROFILE} enable registry
}
```

<br/>

    // При необходимости можно будет удалить профиль и все созданное в профиле следующей командой
    // $ minikube --profile ${PROFILE} stop && minikube --profile ${PROFILE} delete

    // Стартовать остановленный minikube
    // $ minikube --profile ${PROFILE} start