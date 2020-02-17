# Linux Diag Commands

I use some commands in my bash scripts to diagnose services and resources, here there are:

* Check Systemd Service State

```sh
$ systemctl show -p SubState SERVICE_NAME | cut -d '=' -f 2
$ systemctl show -p Result SERVICE_NAME | cut -d '=' -f 2
```

* Check last *N line of* of Systemd Service log which writes to journal

```sh
$ journalctl -u SERVICE_NAME | tail -N_LINES
```

* Check port is running

```sh
$ ss -tlnp | grep PORT_NUMBER
```

* Check a directory is exists

```sh
$ if [ -d "DIRECTOR_ADDR" ]; then echo exists; fi
```

* Check a file is exists

```sh
$ if [ -f "FILE_ADDR" ]; then echo exists; fi
```

* Check if port of a remote server is reachable

```sh
$ nc -zv REMOTE_ADDRESS PORT
```

* Check certificate expiration

```sh
$ cat CERT_ADDRESS | openssl x509 -noout -dates
```

* Check if container is running

```sh
$ docker ps -f "id=CONTAINER_ID" -f "status=running" | sed -n '2 p'
```
