systemd\_mon
===========

The [systemd monitoring daemon](https://github.com/joonty/systemd_mon) is a tool to monitor systemd unit states via dbus. This Docker image encapsulates the functionality into a container which can communicate to dbus via volume mounts.

Using This Image
----------------

There are two items that need to be taken into consideration when running this image: 1) communication with dbus, and 2) writing a config file. After creating a directory with a `config.yml`, a typical way to invoke the monitoring daemon would be like this:

    docker run --name systemd_mon -v /var/run/dbus/system_bus_socket:/var/run/dbus/system_bus_socket -v /path/to/config/dir:/etc/systemd_mon -d tylerjl/systemd_mon

This will start the daemon and watch for unit state on the volume mounted dbus socket.

See the docs for systemd\_mon to find how to properly configure the daemon.

Note: It *is* possible to configure systemd\_mon dynamically with environment variables and parsing/writing the config at runtime, but it feels pretty hacky in practice, so it's probably a good idea to avoid it.
