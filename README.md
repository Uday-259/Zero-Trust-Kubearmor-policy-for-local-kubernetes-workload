## KubeArmor – Local Kubernetes Cluster Setup

## Project Overview
--This project demonstrates how to deploy KubeArmor in a local Kubernetes cluster (Docker Desktop with WSL2) for runtime security and workload protection.

## KubeArmor provides:
--Runtime enforcement of security policies (process, file, network).

--Container & host-level observability.

--Fine-grained access control for workloads.

## This repo contains:
--Official CRD and DaemonSet YAMLs.

--Example security policies.

--Sample test applications.

## A step-by-step README for Helm & YAML deployment.
--Use below command to directly install helm repo locally in your wsl.
-- curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

--Install kubectl using this command.
-- sudo snap install kubectl --classic

--Now deploy the helm chart to the cluster by using this command.
-- helm install my-wisecow ./wisecow-chart

-- Now install kubearmor with the help of this command, automatically crd and daemonset will get installed.
-- helm upgrade --install kubearmor kubearmor/kubearmor -n kubearmor --create-namespace

--Now create your own sample policy and apply it.
--Check if all the policies and daemon file is created by using these commands.
-- kubectl get crds | grep kubearmor
-- kubectl get daemonset -n kubearmor

--To check which pods are running in kubearmor namespace, use this command.
-- kubectl get pods -n kubearmor --show-labels

-- Now open any pod and try running the blocked operation inside the pod
--kubectl exec -it wisecow-deployment-59b65dcd-c26gd -- /bin/bash

-- Now to check the logs and violations, use this command.
--kubectl logs -n kubearmor kubearmor-h74df
