# Runbook

## Is it up?

    kubectl get deployment notification-api --namespace <development|production>
    kubectl port-forward deployment/notification-api 8000:8000 --namespace development
    curl localhost:8000/healthz

## Restart

    kubectl rollout restart deployment/notification-api --namespace <namespace>

## Roll back

Revert the tag bump commit in `wasp-foundry/gitops` (`apps/notification-api/overlays/<env>`); the deployment follows the overlay.
