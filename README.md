# Our changes
Instead of actually executing a metaflow spec this version just generates an Argo workflow YAML on stdout which can then in turn orchestrate the whole DAG on top of Argo instead of orchestrating it natively via metaflow runtime.

## Limitations
* currently not parsing the DAG properly; just sequentializing all steps (not exploiting potential concurrencies)
* template is currently fixed to a python image; this needs more flexibility in the final version
* no step placeholders for resource requirements
* if input paths exceed 32k characters we cut off atm
* AWS secrets are visible on pod level
* current implementation does not support fanout via foreach as it's fully static and doesn't happen at runtime; for a proper fanout we would either need a mini orchestration in a pod (then again we would orchestrate without argo) or not try to generate the whole workflow statically or do orchestrate it via several argo workflows running in sequence (whereas workflow B is only generated when results of workflow A are known for a overall flow of ... -> A -> B -> ...)

# Metaflow

Metaflow is a human-friendly Python library that helps scientists and engineers build and manage real-life data science projects. Metaflow was originally developed at Netflix to boost productivity of data scientists who work on a wide variety of projects from classical statistics to state-of-the-art deep learning.

For more information, see [Metaflow's website](https://metaflow.org).

## Getting Started

Getting up and running with Metaflow is easy. Install metaflow from [pypi](https://pypi.org/project/metaflow/):

>```sh
>pip install metaflow
>```

and access tutorials by typing:

>```sh
>metaflow
>```

## Get in Touch
There are several ways to get in touch with us:

* Open an issue at: https://github.com/Netflix/metaflow 
* Email us at: help@metaflow.org
* Chat with us on: http://chat.metaflow.org 

## Kubernetes Plugin Documentation / Demo
https://github.com/valayDave/metaflow-kube-demo

## How to Setup Kuberentes to Work with Metaflow 
https://github.com/valayDave/metaflow-on-kubernetes-docs
