
# ansible-ecs

Ansible role to install ECS agent on servers

## Role Variables

### Custom variables

**ecs_config**

Disable or enable the configuration of the ECS agent (/etc/ecs/ecs.config), in order to join cluster, select auth, etc.

default: ``false``

**ecs_detach**

Enable detached mode to leave the container running in background. If disabled, fail unless the process exits cleanly.

default: ``true``

**ecs_state**

Assert the container's desired state. "present" only asserts that the matching containers exist. "started" asserts that the matching containers both exist and are running, but takes no action if any configuration has changed. "reloaded" (added in Ansible 1.9) asserts that all matching containers are running and restarts any that have any images or configuration out of date. "restarted" unconditionally restarts (or starts) the matching containers. "stopped" and '"killed" stop and kill all matching containers. "absent" stops and then' removes any matching containers.

default: ``started``

**ecs_restart_policy**

Container restart policy.
The 'unless-stopped' choice is only available starting in Ansible 2.1 and for Docker 1.9 and above.

default: ``always``

**ecs_version**

Version of the ECS agent docker image that should be running on the host

default: ``latest``

**ecs_network_mode**

Network mode for the launched container: bridge, none, container:<name|id>
or host. Requires docker >= 0.11.

default: ``host``

**ecs_volumes**:

List of volumes to mount within the container
Use docker CLI-style syntax: /host:/container[:mode]
You can specify a read mode for the mount with either ro or rw. Starting at version 2.1, SELinux hosts can additionally use z or Z mount options to use a shared or private label for the volume.

default: ``[ /var/run/docker.sock:/var/run/docker.sock, /var/log/ecs/:/log, /var/lib/ecs/data:/data ]``

### Environment variables

The other variables are not documented here because they are all environment variables extracted from [the ECS agent documentation](https://github.com/aws/amazon-ecs-agent#environment-variables).

## License

Copyright (c) We Are Interactive

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

## Author Information

Hugo Rosnet at Cycloid.io
