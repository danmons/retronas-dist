# RetroNAS Docker All-In-One

Everyone wants docker, lets document the challenges with an 'All-In-One' docker image for RetroNAS, right now thats the only way forward without a complete rarchitecture of the project.

## Challenges

| Item      | Problem | Responsibilty |
| ----------- | ----------- | ---------- |
| Ports | Services may conflict with host ports and cannot be run on alt ports if deployed on a existing infra (i.e. Samba+NAS) | Community integration |
| Configuration  | Configuration locations are not standardised and are left up to the service, therefore persistence through volume mapping is not achievabke at this time  | - | 
| Services | RetroNAS is designed to be flexible, as such services are intended to be installed on an as needed basis. In an AIO deployment, this would mean services will not persist, see Configuration with volumes entry, it is unreasonable to think this can be handled in the base image | - |
| Text UI | The TUI would need to be accessed through `docker exec -it retronas retronas` | - |
| Web UI | Not currently available/funcitonal so any reliance on thia is misplaced  | - |
| Data Directory | Easily mapped to a volume for persistence | OK |