# RetroNAS Docker All-In-One (aio)

Everyone wants docker, lets document the challenges with an 'All-In-One' docker image for RetroNAS, right now aio is the only way forward without a complete re-architecture of the project.

## Challenges

| Item      | Problem | Responsibilty |
| ----------- | ----------- | ---------- |
| Ports | Services may conflict with host ports and cannot be run on alt ports if deployed on a existing infra (i.e. Samba+NAS) | Community integration |
| Configuration  | Configuration locations are not standardised and are left up to the service, therefore persistence through volume mapping is not achievabke at this time  | - | 
| Services | RetroNAS is designed to be flexible, as such services are intended to be installed on an as needed basis. In an aio deployment, this would mean services will not persist as they are installed into the container not the image, see Configuration with volumes entry. it is unreasonable to think this can be handled in a base image, that could be published to dockerhub | - |
| Text UI | The TUI would need to be accessed through `docker exec -it retronas retronas` | - |
| Web UI | Not currently available/funcitonal so any reliance on this is misplaced  | - |
| Data Directory | Easily mapped to a volume for persistence | OK |



## Touch points for vols
```
/opt
/etc
/usr/local
/usr/lib/systemd/system
* multiple system packages
```
Most of these will be breaking for the main system, i'm not even going to pretend to map out the system packages, just add in every dir then realise that if you need a completely persistent container you might as well use a VM.