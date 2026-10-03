# Runbook

## Is it up?

    kubectl get deployment hello-beta --namespace <development|production>
    kubectl port-forward deployment/hello-beta 8000:8000 --namespace development
    curl localhost:8000/healthz

## Restart

    kubectl rollout restart deployment/hello-beta --namespace <namespace>

## Roll back

Revert the tag bump commit in `wasp-foundry/gitops` (`apps/hello-beta/overlays/<env>`); the deployment follows the overlay.
