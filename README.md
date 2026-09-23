# OpenWebRx Installer

Installeer **OpenWebRx** (web-based SDR ontvanger) op Debian/Ubuntu Linux met
dit installatie script. Het installeert alle benodigde dependencies, bouwt
`rtl-sdr`, `libcsdr` en `openwebrx`, en configureert het systeem.

## Wat het doet

1. Installeert systeem dependencies (build-essential, git, libfftw3-dev,
   cmake, libusb-1.0-0-dev, nmap)
2. Klont en bouwt `rtl-sdr` van git.osmocom.org
3. Blacklist de DVB-T driver (`dvb_usb_rtl28xxu`) die conflict geeft met rtl-sdr
4. Klont `openwebrx` en `libcsdr` van GitHub
5. Bouwt en installeert `libcsdr`

## Vereisten

- Debian/Ubuntu Linux
- Root toegang (sudo)
- RTL-SDR hardware (optioneel — software werkt ook zonder)

## Installatie

```bash
chmod +x OpenWebRx-Installer.sh
sudo ./OpenWebRx-Installer.sh
```

## Na installatie

OpenWebRx wordt gebouwd in de `openwebrx/` map. De web interface is
standaard bereikbaar op poort 8073.

Zie de [OpenWebRx documentatie](https://github.com/simonyiszk/openwebrx)
voor configuratie en gebruik.

## License

Zie de upstream licentie van OpenWebRx.

## 🎥 Gource Visualization

De ontwikkelhistorie van dit project in een film:

<video src="https://raw.githubusercontent.com/itsdarklikehell/OpenWebRx-Installer/master/gource.mp4" controls width="100%"></video>

*De video wordt automatisch gegenereerd door de [Gource workflow](.github/workflows/gource.yml) bij elke push.*

Lokale video genereren:
```bash
gource --max-files 1000 --key -800x600 \
  --highlight-users --filename-time 3 --output-framerate 25 \
  -s 0.6 --multi-sampling --auto-skip-seconds 0.1 \
  --stop-at-end --hide mouse,progress -o gource.ppm

ffmpeg -y -r 15 -f image2pipe -vcodec ppm -i gource.ppm \
  -vcodec libx264 -preset medium -pix_fmt yuv420p \
  -crf 1 -threads 0 -bf 0 gource.mp4
```

<!-- workflow trigger: 2026-09-23T02:02:34Z -->
