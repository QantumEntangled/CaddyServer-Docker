# Quick Start
You can run a simple CaddyServer Configuration with the following command:

```bash
$ docker run -d \
		-p 80 -p 443 --name mycaddyserver \
		qantumentangled/CaddyServer-Docker
```

But you might also want to pass in a CaddyFile configuration file that you've already written, do this by adding `-e CADDYFILE=</path/to/CaddyFile>` to your command.

```bash
$ docker run -d \
		-p 80 -p 443 --name mycaddyserver \
		-e CADDYFILE=</path/to/CaddyFile> \
		qantumentangled/CaddyServer-Docker
```

You can edit the CaddyFile later by running

```bash
$ docker cp mycaddyserver:/etc/CaddyFile </path/to/destination>
```

For information on writing your CaddyFile configuration see the [CaddyServer Docs](https://caddyserver.com/docs)

# Full Configuration
To include plugins in CaddyServer you'll need to pass in the names of the plugins you want during initial setup via environment variables

```bash
docker run -d \
		-p 80 -p 443 --name mycaddyserver \
		-e CADDYFILE=</path/to/CaddyFile> \
		-e PLUGINS=<comma,separated,listof,plugins> \
		qantumentangled/CaddyServer-Docker
```

To map a directory from the host machine into the CaddyServer container you can add the `-v </host/path>:</CaddyServer/path>` as well. This is useful if you want to edit your web files from the host, but serve them via the CaddyServer Container.

```bash
docker run -d \
		-p 80 -p 443 --name mycaddyserver \
		-e CADDYFILE=</path/to/CaddyFile> \
		-e PLUGINS=<comma,separated,listof,plugins> \
		-v </path/in/host>:</path/in/CaddyServer> \
		qantumentangled/CaddyServer-Docker
```

\*Note: You could also do this with the CaddyFile but it is not recommended.

For information on writing your CaddyFile configuration see the [CaddyServer Docs](https://caddyserver.com/docs)
