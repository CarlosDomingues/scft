# scft

A repository for studies related to Statistical Consequences of Fat Tails, by Nassim Nicholas Taleb. It consists mostly of JupyterLab Notebooks.

## Hacking

This project uses Docker and Visual Studio Code so it can be easily reproduced. To fire it up locally:

1 - Install Docker.

2 - Install Visual Studio Code.

3 - Watch the GIF:

![Opening a VS Code project inside a container.](docs/startup-guide.gif)

## Browsing

After building the dev environment, it should be possible to browse notebooks in two ways:

1. Opening them directly on Visual Studio Code.

2. [On your favorite browser](http://localhost:8888), after firing up the JupyterLab server:

```shell
jupyter lab --core-mode --ip 0.0.0.0 --port 8888  --no-browser
```

## Bibliography

* [Statistical Consequences of Fat Tails: Real World Preasymptotics, Epistemology, and Applications](https://arxiv.org/pdf/2001.10488)