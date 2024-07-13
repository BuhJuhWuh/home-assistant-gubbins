# home-assistant-gubbins

pretty_solcast_apexchart.yaml is code for a Home Assistant [Apexcharts](https://github.com/RomRider/apexcharts-card) chart to present Solcast data nicely. Can't remember where I pinched the original from, so if it was yours, please tell me! Then it's basically just had lots of adding traces and tinkering with opacities.

![pretty solcast chart](https://private-user-images.githubusercontent.com/113393635/348459898-6677fc13-aa2f-4659-a58d-4635b96328ed.png)

To use, just paste into a new Apexcharts card. For the actual generation trace you'll need to replace the xxxxxxxxxx with your own inverter's serial number in the givtcp entities (2 places, towards the end of the file).
