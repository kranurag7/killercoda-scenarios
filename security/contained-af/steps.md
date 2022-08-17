- Execute all the commands & wait for few minutes till the container starts 

```
git clone https://github.com/genuinetools/contained.af
cd contained.af
```{{exec}}

Prepare the static frontend assets with:

```
make dev
```{{exec}}

Start an isolated Docker instance in the background with:

```
make dind
```{{exec}}

Build and run the server with:
```
make run
```{{exec}}

[ACCESS Here]({{TRAFFIC_HOST1_10000}})