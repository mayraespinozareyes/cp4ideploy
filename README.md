# cp4ideploy - Test

https://www.ibm.com/docs/en/cloud-paks/cp-integration/16.1.0?topic=resources-using-api-product-kubernetes-resource

https://www.ibm.com/docs/en/api-connect/10.0.x?topic=applications-managing-platform-rest-api-keys

https://www.ibm.com/docs/en/api-connect/10.0.8?topic=settings-configuring-api-key

--Ingresar a la instancia de API management  y añadir el path

$URL_APIC/manager/$ORG/apikeys/

--Server Name (Uri)

oc get ManagementCluster --all-namespaces

oc get ManagementCluster $INSTANCE_MC -o json -n cp4i | jq -r '.status.endpoints[] | select(.name=="platformApi")'


--Certificado (secretName)

oc get secret $SECRET_NAME_MGMT -o json -n cp4i | jq -r '.data["ca.crt"]'