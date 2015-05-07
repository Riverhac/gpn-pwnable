## Setup

Run as root:

    # chown -R root:root /path/to/gpn-pwnable
    # chmod 700 /path/to/gpn-pwnable
    # cd /path/to/gpn-pwnable/service
    # make
    # useradd gpn
    # mkdir /home/gpn
    # cd /home/gpn
    # /path/to/gpn-pwnable/service/setup.sh gpn

## Running

### Running the service itself

You can serve the binary via socat or xinetd

#### Option 1: Via `socat`

Run as root:

    # screen -S service
    # cd /path/to/gpn-pwnable/service
    # ./run.sh 0.0.0.0 1234 /home/gpn gpn

#### Option 2: Via `xinetd`

TODO

### Fixing up permissions regularly

To prevent attackers messing up the filesystem and thus rendering the
service unusable, we have to regularly update the filesystem permissions.
For that, we can run the protect.sh script, which fixes up the perms
every second:

Run as root:

    # screen -S protect
    # cd /home/gpn
    # /path/to/gpn-pwnable/service/protect.sh

## Cleanup / Reset

If you want to reset the application state, you need to remove the users
directory. Since it has the +a attribute set, you need to remove it first.
The clean.sh script does the job for you:

    # cd /home/gpn
    # /path/to/gpn-pwnable/service/clean.sh
