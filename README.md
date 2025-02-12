# kubectl duplicate

This app is a plugin for `kubectl`, it allows you to duplicate a running Pod and auto-exec into. The list of Pods is filterable, and you can select the namespace you want.

You can also set these parameters for customization of the duplicate:
 - `cpu`
 - `memory`
 - `ttl`

Already created duplicates remain 4h (by default) and you can exec into them as long they're running.

## Requirements

### For build

- `GoLang v1.16`

### For Usage

- `kubectl`

## Usage

### Help

```shell
usage: kubectl-duplicate [<flags>]

Flags:
      --help                 Show context-sensitive help (also try --help-long and --help-man).
      --all-namespaces       All Namespace
  -t, --ttl=14400            Time to live of pods is seconds
  -n, --namespace="default"  Namespace
  -p, --pod=POD              Pod
  -c, --cpu=CPU              cpu
  -m, --memory=MEMORY        Memory
  -k, --kubeconfig=$HOME/.kube/config  
                             Kube config file (override by env var KUBECONFIG
  -v, --version              Print version
```

### Install

Download latest release from https://github.com/qonto/kubectl-duplicate/releases and extract `kubectl-duplicate` into your `/usr/local/bin` and run `chmod -x /usr/local/bin/kubectl-duplicate`.

### Build

```shell
git clone https://github.com/qonto/kubectl-qonto.git
cd ./kubectl-duplicate
go build
mv kubectl-duplicate /usr/local/bin/
```

For `MacOSC` user:
```shell
xattr -d com.apple.quarantine /usr/local/bin/kubectl-duplicate
```

### Run 

* List pods:

    ```shell
    $ kubectl duplicate
    Search:
    ? Pods: 
      > falcosidekick-5f44cb5bff-94sqc
        falcosidekick-5f44cb5bff-jh9wk
    ```

* List pods with already created duplicates:

    ```shell
    Search: █
    ? Pods: 
        falcosidekick-duplicate-nglvr-f569r [duplicate]
      > falcosidekick-duplicate-kzx9z-kpjh6 [duplicate]
        falcosidekick-duplicate-mtb9x-lb29p [duplicate]
        falcosidekick-5f44cb5bff-94sqc
        falcosidekick-5f44cb5bff-jh9wk
        falcosidekick-ui-867f5d6f7-76lfx

    End: 2021-03-08 01:06:25
    ```

* Filter:

    ```shell
    Search: 94█
    ? Pods: 
      > falcosidekick-5f44cb5bff-94sqc
    ```

## Author

[Thomas Labarussias](https://github.com/Issif)