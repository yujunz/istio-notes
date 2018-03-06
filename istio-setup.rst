###########
Istio Setup
###########

****************************
Tree View of istio-auth.yaml
****************************

.. code: yaml

    Namespace
    ClusterRole to ServiceAccount binding
        istio-pilot-istio-system (ClusterRole)
            - istio-pilot-service-account (ServiceAccount)
            - istio-ingress-service-account
        istio-sideca-injector-istio-system
            - istio-sidecar-injector-service-account
        istio-mixer-istio-system
            - istio-mixer-service-account
        istio-ca-istio-system
            - istio-ca-service-account
        istio-sidecar-istio-system
            - default (temporary solution)
    Mixer
        ConfigMap
        Service
        ServiceAccount
        Deployment
        CustomResourceDefinition
            core (label)
                rules (kind)
                    stdio: accesslog entry => stdio handler (resource)
                    promhttp: http metrics => prometheuses handler
                    promtcp: tcp metrics => prometheuses handler
                    kubeattrgenrulerule => kubernetes attributes => kubernetesenvs handler
                attributemanifests
                    istioproxy
                    kubernetes
            adapter
                circonuses
                deniers
                fluentds
                kubernetesenvs
                    handler
                listcheckers
                memquotas
                noops
                opas (Open Policy Agent)
                prometheuses
                    handler
                rbacs
                servicecontrols
                solarwindses (AppOptics and Papertrail)
                stackdrivers
                statsds
                stdios
                    handler
            instance
                apikeys
                authorizations
                checknothings
                kuberneteses
                    attributes
                listentries
                logentries
                    accesslog
                metrics
                    requestcount
                    requestduration
                    requestsize
                    responsesize
                    tcpbytesent
                    tcpbytereceived
                quotas
                reportnothings
                servicecontrolreports
                tracespans
            rbac
                serviceroles
                servicerolebindings
    ConfigMap: istio
    Pilot
        CustomResourceDefinition
            destinationpolicies
            egressrules
            routerules
            v1alpha2routerules
            destinationrules
            externalservices
        Service
        ServiceAccount
        Deployment
    Ingress
        Service
        ServiceAccount
        Deployment
    CA
        ServiceAccount
        Deployment

The most part in ``istio-auth.yaml`` is custom resource definition.

There are a few other resources created besides pilot and mixer:

- access log
- kubernetes attribute
- http and tcp metrics

***********************
Side Car Auto Injection
***********************

TBD
