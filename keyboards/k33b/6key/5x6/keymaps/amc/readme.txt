sed -e 's/_5x6//g' amc_k33b/amc.json > amc_k33b/amc.LAYOUT.json
util/docker_cmd.sh qmk json2c amc.LAYOUT.json -o amc_k33b/km.c
rm amc.LAYOUT.json

util/docker_build.sh k33b/6key/5x6:amc

picotool load -v k33b_6key_5x6_amc.uf2
picotool reboot
