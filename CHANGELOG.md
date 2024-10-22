# Changelog

All notable changes to from Letta to mythOS will be documented in this file.

## [1.1.0] - 2024-10-22
### Added
- Changed server port to 8082.
- Nginx configuration was interferring with other subdomains, so migrated nginx.conf to host machine (ie. `/etc/nginx/sites-available/`) and commented out the `letta-nginx` container in `compose.yaml`.

### Fixed
- Resolved SSL mismatch issue for multiple subdomains.
- Corrected port conflicts in Docker and Nginx configurations.
- Note: this is temporary and should be migrated back to be handled by docker.

## [1.0.0] - 2024-10-20
### Added
- Forked from original memGPT/Letta repository.
