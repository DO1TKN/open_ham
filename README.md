# open_ham
my hamfiles to share



/etc/systemd/system/rtlsdr.service

start rtlsdr on boot with systemd:

[Unit]
Description=RTL-SDR Server
After=network.target

[Service]
ExecStart=/bin/sh -c "/usr/bin/rtl_tcp -a $(hostname -I):1234"
WorkingDirectory=/home/pi
StandardOutput=inherit
StandardError=inherit
Restart=always

[Install]
WantedBy=multi-user.target


## Direwolf auf pi mit rtlsdr

direwolf-rtl.conf:

CHANNEL 0
MYCALL N0CALL
MODEM 1200

KISSPORT 8001
AGWPORT 8000

rtl_fm -f 144.800M -M fm -s 24000 -l 0 - \
  | direwolf -c ~/direwolf-rtl.conf -r 24000 -n 1 -b 16 -t 0 -
