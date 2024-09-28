# home-assistant-gubbins

Some homegrown home assistant bits and bobs.  Feel free to use as you like.

# Pretty Solcast Apexchart

pretty_solcast_apexchart.yaml is code for a Home Assistant [Apexcharts](https://github.com/RomRider/apexcharts-card) chart to present Solcast data nicely. Can't remember where I pinched the original from, so if it was yours, please tell me! Then it's basically just had lots of adding traces and tinkering with opacities.

<img width="669" alt="Screenshot 2024-09-28 at 10 26 56" src="https://github.com/user-attachments/assets/976f8dcf-ced7-45c9-a2f3-f0684bc03b10">

To use, just paste into a new Apexcharts card. For the actual generation trace you'll need to replace the xxxxxxxxxx with your own inverter's serial number in the givtcp entities (2 places, towards the end of the file).
