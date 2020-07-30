# dcs-python script

This repository contains the logic needed for providing a REST API to the Data Collection and Storage, in order to handle automatically the life cycle of this component (for enabling or disabling the signalling topics, in order to configure properly the Logstash pipelines).

Usage: `sudo python3 dcs_rest_client.py [--dcm_ip_address <dcm_ip_address>] --eve_db_password <password> [--port <port_number>] [--log <log_level>]`

Default DCM IP address is localhost, default port is 8091, and default log level is info.

## Application API

The REST API provided by the `dcs_rest_client.py` script implements the following interface:

| Endpoint | Description | Input | Output |
| --- | --- | --- | --- |
| GET / | Check if this logic is running or not | - | 200 - OK |
| POST /portal/dcs/start_signalling | Create signalling topics and start listening to them | - | 201 - accepted, 400 - error parsing request |
| DELETE /portal/dcs/stop_signalling | Delete signalling topics and stop listening to them | - | 201 - accepted, 400 - error parsing request |

(TODO - OpenAPI)

## Steps to be followed

First of all, install Python 3 in the server which will hold this script.

```shell
sudo apt install python3-pip
```

Then, export some variables related to the language.

```shell
export LC_ALL="en_US.UTF-8"
export LC_CTYPE="en_US.UTF-8"
sudo dpkg-reconfigure locales
```

After this, install the required packages for this Python script, which can be found in the requirements.txt file.

```shell
pip3 install -r requirements.txt
```

Finally, execute the script.

```shell
sudo python3 dcs_rest_client.py --dcm_ip_address localhost --eve_db_password password --port 8091 --log info
```

## Copyright

This work has been done by Telcaria Ideas S.L. for the 5G EVE European project under the [Apache 2.0 License](LICENSE).
