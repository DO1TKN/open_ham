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
