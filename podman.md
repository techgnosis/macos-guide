podman CLI tells other executables to run the container
there's no daemon but `podman` does not launch the container

podman launches `conmon` as the parent process of the container runtime

podman can use any OCI runtime


```
root        1729  0.0  0.1   8388  2236 ?        Ss   22:01   0:00 /usr/bin/conmon --api-version 1 -c 69200ace3fd79c770d17d0e98f381e738ffaf1e7f803a6b6db689b9aca1e20ef -u 69200ace3fd79c770d17d0e98f381e738ffaf1e7f803a6b6db689b9aca1e20ef -r /usr/bin/crun -b /var/lib/containers/storage/overlay-containers/69200ace3fd79c770d17d0e98f381e738ffaf1e7f803a6b6db689b9aca1e20ef/userdata -p /run/containers/storage/overlay-containers/69200ace3fd79c770d17d0e98f381e738ffaf1e7f803a6b6db689b9aca1e20ef/userdata/pidfile -n keen_volhard --exit-dir /run/libpod/exits --persist-dir /run/libpod/persist/69200ace3fd79c770d17d0e98f381e738ffaf1e7f803a6b6db689b9aca1e20ef --full-attach -s -l journald --log-level info --syslog --runtime-arg --log-format=json --runtime-arg --log --runtime-arg=/run/containers/storage/overlay-containers/69200ace3fd79c770d17d0e98f381e738ffaf1e7f803a6b6db689b9aca1e20ef/userdata/oci-log -t --conmon-pidfile /run/containers/storage/overlay-containers/69200ace3fd79c770d17d0e98f381e738ffaf1e7f803a6b6db689b9aca1e20ef/userdata/conmon.pid --exit-command /usr/bin/podman --exit-command-arg --root --exit-command-arg /var/lib/containers/storage --exit-command-arg --runroot --exit-command-arg /run/containers/storage --exit-command-arg --log-level --exit-command-arg info --exit-command-arg --cgroup-manager --exit-command-arg systemd --exit-command-arg --tmpdir --exit-command-arg /run/libpod --exit-command-arg --network-config-dir --exit-command-arg  --exit-command-arg --network-backend --exit-command-arg netavark --exit-command-arg --volumepath --exit-command-arg /var/lib/containers/storage/volumes --exit-command-arg --db-backend --exit-command-arg sqlite --exit-command-arg --transient-store=false --exit-command-arg --runtime --exit-command-arg crun --exit-command-arg --storage-driver --exit-command-arg overlay --exit-command-arg --storage-opt --exit-command-arg overlay.imagestore=/usr/lib/containers/storage --exit-command-arg --storage-opt --exit-command-arg overlay.mountopt=nodev,metacopy=on --exit-command-arg --events-backend --exit-command-arg journald --exit-command-arg container --exit-command-arg cleanup --exit-command-arg --rm --exit-command-arg 69200ace3fd79c770d17d0e98f381e738ffaf1e7f803a6b6db689b9aca1e20ef

root        1731  0.0  0.1   4296  3596 pts/0    Ss+  22:01   0:00  \_ bash
```

You can see there that `conmon` runs `crun`


In the Linux VM you find this
`podman system service`
and that starts up an API Listener for remote clients. That is how this works.

You can run `podman system connection list` to see the SSH connections that connect the sockets together



* Linux VM has a socket at `/run/podman/podman.sock`
* Linux VM has `podman system service` process running and listening to that socket
* macOS has a socket in `/var/folders`. You can find the location with `podman machine inspect` at `ConnectionInfo.PodmanSocket.Path`
* Those two sockets are connected by an SSH tunnel. Any data sent to the socket in macOS is sent to the socket in the Linux VM
* podman CLI sends commands to `podman system service` which runs `conman` which run `crun` to launch the process in the container

By default all podman containers launch on a bridge network called `podman`
All containers in a bridge network can reach other containers and the internet throught the host
Containers in one bridge network can reach containers in other bridge networks