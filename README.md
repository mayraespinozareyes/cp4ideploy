# cp4ideploy - Test

https://www.ibm.com/docs/en/cloud-paks/cp-integration/16.1.0?topic=resources-using-api-product-kubernetes-resource

https://www.ibm.com/docs/en/api-connect/10.0.x?topic=applications-managing-platform-rest-api-keys

https://www.ibm.com/docs/en/api-connect/10.0.8?topic=settings-configuring-api-key

--Ingresar a la instancia de API management  y añadir el path

$URL_APIC/manager/$ORG/apikeys/



--Server Name (Uri)

oc get ManagementCluster --all-namespaces

oc get ManagementCluster $INSTANCE_MC -o json -n $NAMESAPCE | jq -r '.status.endpoints[] | select(.name=="platformApi")'

--Ejemplo de resultado:

{
  "name": "platformApi",
  "secretName": "small-mgmt-platform-api", #TOMAR ESTE VALOR PARA OBTENER CERTIFICADO
  "type": "API",
  "uri": ""  #TOMAR ESTE VALOR PARA EL SERVER
}


--Certificado (secretName)

oc get secret $SECRET_NAME_MGMT -o json -n $NAMESAPCE | jq -r '.data["ca.crt"]'



--convertir todos los valores a base64 y crear secret:
kind: Secret
apiVersion: v1
metadata:
  name: connectionapic
  namespace: bn-deploy-prod
data:
  api_key: 
  base_url: 
  grant_type: YXBpX2tleQ==
  trusted_cert: 
type: Opaque



--Secret (Openshift GitOps)

openshift-gitops-cluster

--permitir que openshift gitops administre el namespace

oc label namespace demo-ns argocd.argoproj.io/managed-by=openshift-gitops