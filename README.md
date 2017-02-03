# poormon
not SMART front end to smartctl(smartmontools)
- only show attributes 5, 187, 188, 197, 198 that picked from [Backblaze blog](https://www.backblaze.com/blog/what-smart-stats-indicate-hard-drive-failures/)
- show `devstat` if available
- show DWPD (Drive Write Per Day)


# examples

#### TOSHIBA Consumer Grade HDD
need `root` user or `disk` group
```
$ sudo ./poormon /dev/sdf
Device: TOSHIBA DT01ACA300 (~~)
Capacity: 2794.52 GiB (3000.59 GB)
Power On: 0.17 years (1504 hours, 62.7 days, power cycle 154)
SMART:
    5: Reallocated Sectors Count     : 0
  197: Current Pending Sector Count  : 0
  198: Uncorrectable Sector Count    : 0
Device stat:
  Write: 7.94 TiB (2.91 drive write)
  Read:  9.37 TiB
  Read/Write Ratio:  1.18
  Write per Year: 46.24 TiB/year
  Write per Day: 129.72 GiB/day (0.046 DWPD)
  Read per Year: 54.58 TiB/year
  Read per Day: 153.11 GiB/day
  Read Recovery: 0 corrected, 0 uncorrect
  Interface CRC Errors: 0
  Mechanical Start Failures: 6
```
this consumer grade drive support devstat(cool!).<br>
but another one is ...

#### Seagate Consumer Grade HDD
```
Device: ST2000DL003-9VT166 (~~)
Capacity: 1863.02 GiB (2000.40 GB)
Power On: 2.25 years (19737 hours, 822.4 days, power cycle 2376)
SMART:
    5: Reallocated Sectors Count     : 0
  187: Reported Uncorrectable Errors : 0
  188: Command Timeout               : 2
  197: Current Pending Sector Count  : 0
  198: Uncorrectable Sector Count    : 0
Device stat: not supported
```
this one isn't.<br>
and `Command Timeout: 2`, I need to watch out.

#### TOSHIBA Consumer Grade SSD
```
Device: TOSHIBA THNSNJ256GCSU (~~)
Capacity: 238.47 GiB (256.06 GB)
Power On: 0.41 years (3597 hours, 149.9 days, power cycle 406)
SMART:
    5: Reallocated Sectors Count     : 0
  197: Current Pending Sector Count  : 0
Device stat:
  Write: 1669.96 GiB (7.00 drive write)
  Read:  1103.65 GiB
  Read/Write Ratio:  0.66
  Write per Year: 3.97 TiB/year
  Write per Day: 11.14 GiB/day (0.047 DWPD)
  Read per Year: 2.62 TiB/year
  Read per Day: 7.36 GiB/day
  Endurance Indicator: 1% used
  Interface CRC Errors: 0
```
many of modern SSD supports `Endurance Indicator`.<br>
T13 explain
> percentage of device life used based on the actual device usage and the manufacturer's prediction of device life.
<br>

#### HGST Enterprise Grade HDD (old)
```
Device: Hitachi HUA722010CLA330 (~~)
Capacity: 931.51 GiB (1000.20 GB)
Power On: 3.73 years (32713 hours, 1363.0 days, power cycle 50)
SMART:
    5: Reallocated Sectors Count     : 0
  197: Current Pending Sector Count  : 0
  198: Uncorrectable Sector Count    : 0
Device stat:
  Write: 7.06 TiB (7.76 drive write)
  Read:  212.98 TiB
  Read/Write Ratio: 30.15
  Write per Year: 1.89 TiB/year
  Write per Day: 5.31 GiB/day (0.006 DWPD)
  Read per Year: 57.03 TiB/year
  Read per Day: 160.00 GiB/day
  Read Recovery: 1441 corrected, 0 uncorrect
  Interface CRC Errors: 0
  Mechanical Start Failures: 4294967295
```
this just about $25 at junk shop.<br>
over 30000 hours, but still operational.<br>
I need to be careful because of Mechanical-something looks wrong.

## TODO

- temperature stuff?



