# cp4ideploy - Test


--Ingresar a la instancia de API management  y añadir el path

$URL_APIC/manager/$ORG/apikeys/

--Server Name (Uri)

oc get ManagementCluster --all-namespaces

oc get ManagementCluster $INSTANCE_MC -o json -n cp4i | jq -r '.status.endpoints[] | select(.name=="platformApi")'


--Certificado (secretName)

oc get secret $SECRET_NAME_MGMT -o json -n cp4i | jq -r '.data["ca.crt"]'