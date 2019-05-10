# EasyNTPClient 

[![Collaborizm](https://img.shields.io/badge/Collaborizm-Join%20now-blue.svg)](https://www.collaborizm.com/)
[![Build Status](https://travis-ci.org/aharshac/EasyNTPClient.svg?branch=master)](https://travis-ci.org/aharshac/EasyNTPClient)    

Arduino library to read time from Network Time Protocol (NTP) servers.

&nbsp;

## Features
- Handles all heavy lifting involved with managing connections to and parsing time from an NTP server.
- As easy as providing a **UDP** object to the constructor during initialization.
- Works on **Arduino** and **ESP8266**.

&nbsp;

## Changes Compared to Root
- If time update from NTP server fails, time is not set to 0 but kept as last known
- Added functions to get info, if time update failed, and time since last update
- Possible to set update interval (default 60 secs) with init call or separate function

&nbsp;

## Examples    
1. **NodeMCU**    
Using EasyNTPClient on a NodeMCU (ESP8266)     

2. **ArduinoEspWifiShield**    
Using EasyNTPClient on an Arduino UNO with an ESP-01 (ESP8266) WiFi module.    
By [**Claran Martis**](https://www.collaborizm.com/profile/SJne7FcMg)

&nbsp;

## Reference
### Class **EasyNTPClient**
#### Initialization ####
1. Possible calls
```c
EasyNTPClient(UDP &udp);
EasyNTPClient(UDP &udp, const char* serverPool);
EasyNTPClient(UDP &udp, const char* serverPool, int offset);
EasyNTPClient(UDP &udp, const char* serverPool, int offset, unsigned int updateInterval);
```

2. Parameters
```
    udp:             Reference to an UDP object.
    serverPool:      NTP server pool domain name. Default = "pool.ntp.org".
    offset:          Difference from UTC in seconds. Default = 0.
    updateInterval:  Update interval in seconds. Default = 60.
                     (getUnixTime will return internal unix time before the update interval is reached)
```

3. Return
```c
    EasyNTPClient object
```

#### Methods ###    
Get time in UNIX format
```c
unsigned long getUnixTime();

Returns:
    UTC time in UNIX time format (seconds)
```

Set update interval
```c
void setInterval(unsigned int updateInterval);

Parameters:
    updateInterval: Update interval in seconds. Default = 60.
```

Last update successful
```c
bool wasUpdated()

Returns:
    TRUE:  If last update was successful
    FALSE: If last update was not successful
```

Time since last successful update
```c
unsigned int sinceUpdate()

Returns:
    Time in seconds since the last successful update.
```

Get time offset
```c
int getTimeOffset()

Returns:
    EasyNTPClient object.
```

Set time offset
```c
void setTimeOffset(int offset);

Parameters:
    offset: Difference from UTC in seconds.
```
