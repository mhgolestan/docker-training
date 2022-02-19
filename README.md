# docker-training

## Docker cheat sheet

### Working with Docker Images :

<code>docker image ls</code>
<br />
<code>docker image inspect hello-world</code>

use <mark>jq</mark> for better inspection:
<br />
The environment variables:
<br />
<code>docker image inspect hello-world | jq '.[].Config.Env'</code>
<br />
startup command on the container:
<br />
<code>docker image inspect hello-world | jq '.[].Config.Cmd'</code>
<br />
Layers associated with the image
<br />
<code>docker image inspect hello-world | jq '.[].RootFS.Layers'</code>
<br />

### Another example with nginx

<code>docker pull nginx:stable</code>
<br />
<code>docker run -p 80:80 nginx</code>
<br />
The first parameter after the flag is the port on the Docker host which must be published, and the second parameter refers to the port within the container.
You can confirm that the image publishes the port using docker inspect:
<code>docker image inspect nginx | jq '.[].Config.ExposedPorts'</code>

<br />
or we can change the port on which the service is published on the Docker host by changing the first parameter after the -p flag, as follows:
<code>docker run -p 8080:80 nginx</code>
<br />
<code>curl http://localhost:8080</code>
