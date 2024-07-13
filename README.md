# home-assistant-gubbins

pretty_solcast_apexchart.yaml is code for a Home Assistant [Apexcharts](https://github.com/RomRider/apexcharts-card) chart to present Solcast data nicely. Can't remember where I pinched the original from, so if it was yours, please tell me! Then it's basically just had lots of adding traces and tinkering with opacities.

To use, just paste into a new Apexcharts card. For the actual generation trace you'll need to replace the xxxxxxxxxx with your own inverter's serial number in the givtcp entities (2 places, towards the end of the file).
