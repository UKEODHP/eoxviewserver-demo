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

Where <stac-item> is the stringified ceda-stac.json contents.
Currently this gives the error: *pystac.errors.STACTypeError: JSON (id = stac-fastapi) does not represent a Item instance.*