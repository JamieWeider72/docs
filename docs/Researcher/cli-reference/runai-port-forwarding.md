# runai port-forward

## Description

Forward one or more local ports to the selected job. The forwarding session ends when the selected job terminates.

To use `runai port-forward`, install and configure the [Install the Run:ai Command-line Interface](../../admin/researcher-setup/cli-install.md)

!!!Note

    1. You need to use port forwarding to get to the SSH on the server.
    
    2. You must use the SSH port that the server is listening to.
 
    3. You must use a local session for port forwarding to the SSH port of the server. This is to ensure that you do not leave SSH sessions open for too long.

    4. If a port forwarding session is terminated, all connections to that session will be terminated. You will need to rerun the `port-forward` command to reinstate port forwarding. Then, all previously connected users must reconnect.

### Examples

1. Port forward connections from localhost:8080 to <job-name> on port 8090.

    `runai port-forward <job-name> --port 8080:8090`

2. Port forward connections from 0.0.0.0:8080 to <job-name> on port 8080.

    `runai port-forward <job-name> --port 8080 --address 0.0.0.0 [require privileges]`

3. Port forward multiple connections from localhost:8080 to <job-name> on port 8090 and localhost:6443 to <job-name> on port 443.

    `runai port-forward <job-name> --port 8080:8090  --port 6443:443`

### Global flags

`--loglevel <string>`&mdash;Set the logging level. Choose: <debug|info|warn|error> (default "info").

`-p | --project <string>`&mdash;Specify the project name. To change the default project use `runai config project <project name>`.

### Flags

`--address <string> | [local-interface-ip\host] |localhost | 0.0.0.0 [privileged]`&mdash;The listening address of your local machine. (default "localhost").

`-h | --help`&mdash;Help for the command.

`--port`&mdash;forward ports based on one of the following arguments:

  * `<stringArray>`&mdash;a list of port forwarding combinations.

  * `[local-port]:[remote-port]`&mdash;different local and remote ports.

  * `[local-port=remote-port]`&mdash;the same port is used for both local and remote.

***Filter based flags***

`--mpi`&mdash;search **only** for mpi jobs.

`--interactive`&mdash;search **only** for interactive jobs.

`--pytorch`&mdash;search **only** for pytorch jobs.

`--tf`&mdash;search **only** for tensorflow jobs.

`--train`&mdash;search **only** for training jobs.