# Recycling Logistics Infrastructure

Terraform and operating documentation for the Recycling Logistics MVP on Oracle Cloud Always Free.

## Scope

- One Ubuntu Ampere A1 ARM64 VM (up to 4 OCPUs / 24 GB).
- Public VCN/subnet, Internet Gateway and route table.
- OCI security list: public HTTP/HTTPS and SSH limited to approved CIDRs.
- Cloud-init installs Docker Engine and Docker Compose plugin.
- Application deployment remains in [DungeonEaters/recycling-logistics](https://github.com/DungeonEaters/recycling-logistics): GitHub Actions builds images in GHCR; manual deployment pulls those images into this VM.

## Layout

```text
environments/production/  # Terraform root for shared Always Free VM
```

The VM hosts distinct Compose stacks for `test` and `production`. They share host capacity, but have separate directories, networks, volumes, `.env` files and subdomains.

## First provision

See [environments/production/README.md](environments/production/README.md). Never commit OCI API keys, SSH private keys, `.tfvars`, `.env`, or Terraform state.
