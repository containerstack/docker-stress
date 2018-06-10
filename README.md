# Alpine based Stress Docker image

## What is Stess;
Stress is a deliberately simple workload generator for POSIX systems. It imposes a configurable amount of CPU, memory, I/O, and disk stress on the system.

## How to run the container;
In this example the stress app will consume 2 cores for the duration of 60 seconds, after the 60 seconds the container will be stopped and removed from the system.

````
$ docker run -ti --rm containerstack/stress:1.0.4 \
    stress \
    --cpu 2 \
    --timeout 60s
````

In this example we are running a CPU stress test over 2 cores for 60 seconds

## Options

Stress has a couple of options, in the example above we are only using the CPU.
However other system components can also be tested, check out the following switch options:

````
Usage: stress [OPTION [ARG]] ...
 -?, --help         show this help statement
     --version      show version statement
 -v, --verbose      be verbose
 -q, --quiet        be quiet
 -n, --dry-run      show what would have been done
 -t, --timeout N    timeout after N seconds
     --backoff N    wait factor of N microseconds before work starts
 -c, --cpu N        spawn N workers spinning on sqrt()
 -i, --io N         spawn N workers spinning on sync()
 -m, --vm N         spawn N workers spinning on malloc()/free()
     --vm-bytes B   malloc B bytes per vm worker (default is 256MB)
     --vm-stride B  touch a byte every B bytes (default is 4096)
     --vm-hang N    sleep N secs before free (default none, 0 is inf)
     --vm-keep      redirty memory instead of freeing and reallocating
 -d, --hdd N        spawn N workers spinning on write()/unlink()
     --hdd-bytes B  write B bytes per hdd worker (default is 1GB)

Example: stress --cpu 8 --io 4 --vm 2 --vm-bytes 128M --timeout 10s
````

## Docker images;
The Docker Hub Auto Build is based on this repository can be found [here](https://hub.docker.com/r/containerstack/stress/).

### Alpine source image;
This container image is based on the containerstack/alpine image (AMD64).
The Docker Hub Auto Build of this repo can be found [here](https://hub.docker.com/r/containerstack/alpine/), and the Bitbucket repo can be found [here](https://bitbucket.org/containerstack/docker-stress/).
