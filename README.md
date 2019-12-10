# rclone-gui

Sample run command:

```bash
docker run -d --name=rclone-gui \
-v /config:/config \
-v /media:/media \
-e GROUP_ID=99 -e USER_ID=100 -e TZ=America/Chicago \
-p 5572:5572 \
d2dyno/rclone-gui:latest
```

Go to `http://your-host-ip:5572` to access the Rclone GUI.

### Environment Variables

To customize some properties of the container, the following environment
variables can be passed via the `-e` parameter (one for each variable).  Value
of this parameter has the format `<VARIABLE_NAME>=<VALUE>`.

| Variable       | Description                                  | Default |
|----------------|----------------------------------------------|---------|
|`RCUSER`|  Username to be used to authenticate into the web interface. |
|`RCPASS`|  Password to be used to authenticate into the web interface. |

### Data Volumes

The following table describes data volumes used by the container.  The mappings
are set via the `-v` parameter.  Each mapping is specified with the following
format: `<HOST_DIR>:<CONTAINER_DIR>[:PERMISSIONS]`.

| Container path  | Permissions | Description |
|-----------------|-------------|-------------|
|`/config`| rw | This is where the application stores its configuration, log and any files needing persistency. |
|`/media`| rw | This is where downloaded files are stored, or where you put files in your host for uploading. |

### Ports

Here is the list of ports used by the container.  They can be mapped to the host
via the `-p` parameter (one per port mapping).  Each mapping is defined in the
following format: `<HOST_PORT>:<CONTAINER_PORT>`.  The port number inside the
container cannot be changed, but you are free to use any port on the host side.

| Port | Mapping to host | Description |
|------|-----------------|-------------|
| 5572 | Mandatory | Port used to access the application's GUI via the web interface. |
