# <a name="QuickStart"></a>Quick start

* [Quick start](#QuickStart)
    - [Getting Malcolm](#GetMalcolm)
    - [User interface](#UserInterfaceURLs)

## <a name="GetMalcolm"></a>Getting Malcolm

For a `TL;DR` example of downloading, configuring, and running Malcolm on a Linux platform, see [Installation example using Ubuntu 22.04 LTS](ubuntu-install-example.md#InstallationExample).

The scripts to control Malcolm require Python 3. The [`install.py`](malcolm-config.md#ConfigAndTuning) script requires the [requests](https://docs.python-requests.org/en/latest/) module for Python 3, and will make use of the [pythondialog](https://pythondialog.sourceforge.io/) module for user interaction (on Linux) if it is available.

### Source code

The files required to build and run Malcolm are available on its [GitHub page]({{ site.github.repository_url }}/tree/{{ site.github.build_revision }}). Malcolm's source code is released under the terms of a permissive open source software license (see [`License.txt`]({{ site.github.repository_url }}/blob/{{ site.github.build_revision }}/License.txt)  for the terms of its release).

### Building Malcolm from scratch

The `build.sh` script can build Malcolm's Docker images from scratch. See [Building from source](development.md#Build) for more information.

### Initial configuration

You must run [`auth_setup`](authsetup.md#AuthSetup) prior to pulling Malcolm's Docker images. You should also ensure your system configuration and `docker-compose.yml` settings are tuned by running `./scripts/install.py` or `./scripts/install.py --configure` (see [System configuration and tuning](malcolm-config.md#ConfigAndTuning)).
    
### Pull Malcolm's Docker images

Malcolm's Docker images are periodically built and hosted on [GitHub](https://github.com/orgs/idaholab/packages?repo_name=Malcolm). If you already have [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/), these prebuilt images can be pulled by navigating into the Malcolm directory (containing the `docker-compose.yml` file) and running `docker-compose pull` like this:
```
$ docker-compose pull
Pulling api               ... done
Pulling arkime            ... done
Pulling dashboards        ... done
Pulling dashboards-helper ... done
Pulling file-monitor      ... done
Pulling filebeat          ... done
Pulling freq              ... done
Pulling htadmin           ... done
Pulling logstash          ... done
Pulling name-map-ui       ... done
Pulling netbox            ... done
Pulling netbox-postgresql ... done
Pulling netbox-redis      ... done
Pulling nginx-proxy       ... done
Pulling opensearch        ... done
Pulling pcap-capture      ... done
Pulling pcap-monitor      ... done
Pulling suricata          ... done
Pulling upload            ... done
Pulling zeek              ... done
```

You can then observe that the images have been retrieved by running `docker images`:
```
$ docker images
REPOSITORY                                                     TAG               IMAGE ID       CREATED      SIZE
ghcr.io/idaholab/malcolm/api                                              23.04.0           xxxxxxxxxxxx   3 days ago   158MB
ghcr.io/idaholab/malcolm/arkime                                           23.04.0           xxxxxxxxxxxx   3 days ago   816MB
ghcr.io/idaholab/malcolm/dashboards                                       23.04.0           xxxxxxxxxxxx   3 days ago   1.02GB
ghcr.io/idaholab/malcolm/dashboards-helper                                23.04.0           xxxxxxxxxxxx   3 days ago   184MB
ghcr.io/idaholab/malcolm/file-monitor                                     23.04.0           xxxxxxxxxxxx   3 days ago   588MB
ghcr.io/idaholab/malcolm/file-upload                                      23.04.0           xxxxxxxxxxxx   3 days ago   259MB
ghcr.io/idaholab/malcolm/filebeat-oss                                     23.04.0           xxxxxxxxxxxx   3 days ago   624MB
ghcr.io/idaholab/malcolm/freq                                             23.04.0           xxxxxxxxxxxx   3 days ago   132MB
ghcr.io/idaholab/malcolm/htadmin                                          23.04.0           xxxxxxxxxxxx   3 days ago   242MB
ghcr.io/idaholab/malcolm/logstash-oss                                     23.04.0           xxxxxxxxxxxx   3 days ago   1.35GB
ghcr.io/idaholab/malcolm/name-map-ui                                      23.04.0           xxxxxxxxxxxx   3 days ago   143MB
ghcr.io/idaholab/malcolm/netbox                                           23.04.0           xxxxxxxxxxxx   3 days ago   1.01GB
ghcr.io/idaholab/malcolm/nginx-proxy                                      23.04.0           xxxxxxxxxxxx   3 days ago   121MB
ghcr.io/idaholab/malcolm/opensearch                                       23.04.0           xxxxxxxxxxxx   3 days ago   1.17GB
ghcr.io/idaholab/malcolm/pcap-capture                                     23.04.0           xxxxxxxxxxxx   3 days ago   121MB
ghcr.io/idaholab/malcolm/pcap-monitor                                     23.04.0           xxxxxxxxxxxx   3 days ago   213MB
ghcr.io/idaholab/malcolm/postgresql                                       23.04.0           xxxxxxxxxxxx   3 days ago   268MB
ghcr.io/idaholab/malcolm/redis                                            23.04.0           xxxxxxxxxxxx   3 days ago   34.2MB
ghcr.io/idaholab/malcolm/suricata                                         23.04.0           xxxxxxxxxxxx   3 days ago   278MB
ghcr.io/idaholab/malcolm/zeek                                             23.04.0           xxxxxxxxxxxx   3 days ago   1GB
```

### Import from pre-packaged tarballs

Once built, the `malcolm_appliance_packager.sh` script can be used to create pre-packaged Malcolm tarballs for import on another machine. See [Pre-Packaged Installation Files](development.md#Packager) for more information.

## Starting and stopping Malcolm

Use the scripts in the `scripts/` directory to start and stop Malcolm, view debug logs of a currently running
instance, wipe the database and restore Malcolm to a fresh state, etc.

## <a name="UserInterfaceURLs"></a>User interface

A few minutes after starting Malcolm (probably 5 to 10 minutes for Logstash to be completely up, depending on the system), the following services will be accessible:

* [Arkime](https://arkime.com/): [https://localhost:443](https://localhost:443)
* [OpenSearch Dashboards](https://opensearch.org/docs/latest/dashboards/index/): [https://localhost/dashboards/](https://localhost/dashboards/) or [https://localhost:5601](https://localhost:5601)
* [Capture File and Log Archive Upload (Web)](upload.md#Upload): [https://localhost/upload/](https://localhost/upload/)
* [Capture File and Log Archive Upload (SFTP)](upload.md#Upload): `sftp://<username>@127.0.0.1:8022/files`
* [Host and Subnet Name Mapping](host-and-subnet-mapping.md#HostAndSubnetNaming) Editor: [https://localhost/name-map-ui/](https://localhost/name-map-ui/)
* [NetBox](asset-interaction-analysis.md#AssetInteractionAnalysis): [https://localhost/netbox/](https://localhost/netbox/)
* [Account Management](authsetup.md#AuthBasicAccountManagement): [https://localhost:488](https://localhost:488)