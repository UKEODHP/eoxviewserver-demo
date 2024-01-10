# EOx View Server Demo

## Deploy

### Development
```bash
kustomize build base --enable-helm | kubectl apply -f -
```

## Register Item
```bash
kubectl exec -n eox deployment/eoxviewserver-registrar -- registrar --config-file /config.yaml register items <stac-item>
```

Where <stac-item> is the string in base/eoxviewserver/sentinel2_ard-stac-item.txt.

## STAC
### Modifications
1. Add "s2:product_type": "S2MSI1C" to "properties" field.
1. Add "eo:bands": [...] to "properties" field.
1. Rename all "role" fields to "roles" in assets object.
1. Added 'Z' suffix to "properies.datetime".