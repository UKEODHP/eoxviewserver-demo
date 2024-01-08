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
Currently this gives the error:
```
  File "/usr/local/lib/python3.10/dist-packages/registrar/backend/eoxserver.py", line 367, in register
    for product_type in self.product_types:
TypeError: 'NoneType' object is not iterable
```

## STAC
### Modifications
1. Add "s2:product_type": "S2MSI1C" to "properties" field.
1. Add "eo:bands": [...] to "properties" field.
1. Rename all "role" fields to "roles" in assets object.