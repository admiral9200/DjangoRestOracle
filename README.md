# DjangoRestOracle
Django Rest Server with Oracle DB


## Requisites:
```
sudo apt-get install build-essential unzip python-dev libaio-dev
```

Download from:
http://www.oracle.com/technetwork/topics/linuxx86-64soft-092277.html:
instantclient-sdk-linux.x64-12.1.0.2.0.zip
img/pa_gapps-modular-full-5.1-20150315-signed.zip

Unzip and
sudo mv instantclient_12_1 /opt/

export ORACLE_HOME=/opt/instantclient_12_1
cd $ORACLE_HOME
ln -s libclntsh.so.12.1 libclntsh.so
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$ORACLE_HOME
pip install cx_oracle --user

## Test:
import cx_Oracle
from pprint import pprint
db = cx_Oracle.connect(USER, PASSWORD, 'HOSTNAME:1521/DBNAME')
cursor = db.cursor()
cursor.execute('select * from icat4.instrument')
pprint(cursor.fetchall())
