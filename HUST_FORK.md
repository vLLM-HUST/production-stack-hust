# vLLM-HUST fork policy

This repository is the vLLM-HUST thin fork of
[`vllm-project/production-stack`](https://github.com/vllm-project/production-stack).
Upstream remains the source of truth for Router, Helm, CRD, controller, and
autoscaling behavior.

The HUST delta is intentionally limited to:

- reproducible `linux/arm64` build and smoke-test coverage;
- GHCR release carriers owned by `vLLM-HUST`;
- narrowly scoped integration fixes required by vLLM-HUST hosts.

Extension discovery, compatibility decisions, configuration rendering, and
delegated lifecycle operations belong to vLLM-HUST Extension Manager, not this
fork. Publishing is manual and remains disabled until the arm64 validation job
passes on `main`.

The fork does not operate self-hosted GitHub runners. Automated validation uses
GitHub-hosted runners; accelerator and Kubernetes acceptance runs on demand on
separately operated hosts and is recorded as external evidence.

## Synchronizing upstream

```bash
git fetch upstream
git switch main
git merge --ff-only upstream/main
git push origin main
```

HUST changes should remain on focused branches and be proposed upstream when
they are generally useful.
