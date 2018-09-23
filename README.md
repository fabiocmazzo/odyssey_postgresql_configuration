# Configuration of Yandex Odyssey PostgreSQL Connection Pooler

First, build from sources:

git clone git://github.com/yandex/odyssey.git
cd odyssey/
mkdir build
cd build/
cmake -DCMAKE_BUILD_TYPE=Release ..
make

This will build executable in source/odyssey, copy file to a location in your system to use, per example /opt/odyssey/:

mkdir /opt/odyssey
cp source/odyssey /opt/odyssey

Copy example config file from Odyssey repo in same location (or not, you can define path of config file in odyssey startup):

cd ..
cp  ./scripts/debian/config /opt/odyssey

Change connection and database details from config files and run odyssey to test:

/opt/odyssey/odyssey /opt/odyssey/config

Note: if you using md5 hash password, get password hash from database:

SELECT usename, passwd FROM pg_shadow WHERE usename=$1

# Edit init script file (https://raw.githubusercontent.com/yandex/odyssey/master/scripts/debian/init) to add in init.d 

- Change variables ex:
NAME="odyssey"
USER="root"
GROUP="root"
LOGDIR="/opt/odyssey/logs/"
PIDDIR="/opt/odyssey/"
PIDFILE="/opt/odyssey/odyssey_pid"
BINFILE="/opt/odyssey/odyssey"
CONFFILE="/opt/odyssey/config"
CMD="start-stop-daemon --verbose --pidfile $PIDFILE"






