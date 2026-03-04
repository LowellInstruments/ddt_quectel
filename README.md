# Cell shield firmware update

Old cell shield firmware may be from 2017 or 2019 or 2022.

Open terminal window:

```console
su pi
```
Open the minicom terminal:

```console
sudo minicom -D /dev/ttyUSB2 -b 115200
```
Then, when the black screen appears, type (it might not echo) the following (in capitals):

AT+CVERSION

Press Ctrl A + X to leave the minicom connection.

Check /home/pi/li for a ``ddt_quectel`` folder. You might already have it. Otherwise, please do:

```console
cd /home/pi/li;
git clone https://github.com/lowellinstruments/ddt_quectel.git --depth 1
```

If you need to update cell shield firmware version (we have the newest 2022) for ```EG25 modules``` (not EC25) just do:

```console
cd /home/pi/li/ddt_quectel;
unzip QFirehose_Linux_Android_V1.4.13.zip;
unzip EG25GGBR07A08M2G_A0.303.A0.303_2025.zip;
cd QFirehose_Linux_Android_V1.4.13;
make;
sudo ./QFirehose -f ..
```

Instead, for ```EC25 modules``` do:

```console
cd /home/pi/li/ddt_quectel;
unzip QFirehose_Linux_Android_V1.4.13.zip;
unzip cell_fw_2025.zip;
cd QFirehose_Linux_Android_V1.4.13;
make;
sudo ./QFirehose -f ..
```

You might want to re-check the new firmware version again with:

```console
sudo minicom -D /dev/ttyUSB2 -b 115200
```

Then, when the black screen appears, type (it might not echo) the following (in capitals):

AT+CVERSION

Press Ctrl A + X to leave the minicom connection.

Check that the cell connection is working:
```console
ping -I ppp0 www.google.com -4
```

To Install SixFab Shield
```console
cdt
cd _dt_files
sudo ./ppp_install_sixfab.sh
```
