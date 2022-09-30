# Oracle APEX

From [oracle.com](https://apex.oracle.com/):
> Oracle APEX is a low-code development platform that enables you to build scalable, secure enterprise apps, with world-class features, that can be deployed anywhere.

Oracle APEX can be used in [Oracle Cloud](https://apex.oracle.com/en/learn/getting-started/) or installed on an existing Oracle Database.

## Installation

To set up an Oracle Database XE instance, see instructions [here](https://github.com/ojwm/oracle-sqlcl).

[Official APEX 21.2 instructions](https://docs.oracle.com/en/database/oracle/application-express/21.2/htmig/upgrading-apex-within-oracle-db-xe.html#GUID-38805604-3203-4365-B9E0-9347DE5D3D7A).

1. Download the latest [Oracle APEX release](https://www.oracle.com/tools/downloads/apex-downloads.html).

   ```sh
   mkdir /tmp/apex
   cd /tmp/apex
   curl -O https://download.oracle.com/otn_software/apex/apex-latest.zip
   ```

1. Unpack the archive and `cd` to the installer.

   ```sh
   unzip -oq apex-latest.zip
   rm apex-latest.zip
   cd apex
   ```

1. Connect to database as `SYSDBA`.

   ```sh
   sql SYS@XEPDB1 as SYSDBA
   ```

1. Install APEX. This will take some time.

   ```text
   @apexins.sql SYSAUX SYSAUX TEMP /i/
   ```

1. Change the `ADMIN` password.

   ```text
   @apxchpwd.sql
   ```

1. Create REST database users.

   ```text
   @apex_rest_config.sql
   ```

1. Exit and connect to the container database.

   ```sh
   sql SYS as SYSDBA
   ```

1. Unlock the `xdb` user.

   ```sql
   ALTER USER xdb ACCOUNT UNLOCK;
   ```

Thank you for installing Oracle APEX 22.1.0

Oracle APEX is installed in the APEX_220100 schema.

The structure of the link to the Oracle APEX administration services is as follows:
<http://host:port/ords/apex_admin>

The structure of the link to the Oracle APEX development interface is as follows:
<http://host:port/ords>
