# home-assistant-gubbins

Some homegrown home assistant bits and bobs.  Feel free to use as you like.

## Pretty Solcast Apexchart

pretty_solcast_apexchart.yaml is code for a Home Assistant [Apexcharts](https://github.com/RomRider/apexcharts-card) chart to present Solcast data nicely. Can't remember where I pinched the original from, so if it was yours, please tell me! Then it's basically just had lots of adding traces and tinkering with opacities.

<img width="669" alt="Screenshot 2024-09-28 at 10 26 56" src="https://github.com/user-attachments/assets/976f8dcf-ced7-45c9-a2f3-f0684bc03b10">

To use, just paste into a new Apexcharts card. For the actual generation trace you'll need to replace the xxxxxxxxxx with your own inverter's serial number in the givtcp entities (2 places, towards the end of the file).

## Predbat Heat Pump Consumption Forecast

Uses the 24hr forecast temperatures from the [Met.no integration](https://www.home-assistant.io/integrations/met) to calculate predicted heat pump usage, formatting the result in a form suitable for input to [Predbat's Load Forecast input](https://springfall2008.github.io/batpred/apps-yaml/#load-forecast).  See also some discussion [here](https://github.com/springfall2008/batpred/discussions/837).

### 1. Calculate your home's heat curve

Plot your HP's total energy consumption vs daily average outside temperature in your favourite spreadsheet app.  For my Vaillant Arotherm, all of this info is available from the myVAILLANT app.  You'll want a decent spread of data for this, though you can always update it as you go - I started with a month or so's data back in Feb/March, but the warm part of the chart has filled out nicely over the summer - we'll see how the left-hand side fills out this winter.  If you don't have an outdoor temperature sensor as part of your heat pump setup, you can get reasonable results from a nearby weather station - try something like [Wunderground](https://www.wunderground.com).

<img width="587" alt="Screenshot 2024-09-28 at 10 36 52" src="https://github.com/user-attachments/assets/ca9d948f-68d9-4d72-b478-2784b5e79e1f">

Fit a trendline.  Quadratic was the best-looking fit for me.  Show the equation, and note the three coefficients (a, b and c, from y = ax^2 + bx + c), being careful of +/- signs.

### 2. Home Assistant setup

Grab the template from [HP_energy_prediction.yaml](https://github.com/BuhJuhWuh/home-assistant-gubbins/blob/main/HP_energy_prediction.yaml).  Substitute in your coefficients a, b and c in lines 22-24.

Find the relevant section in Predbat's apps.yaml, and point it towards your new template:

```
  # Load forecast can be used to add to the historical load data (heat-pump)
  # To link to Predheat
  # Data must be in the format of 'last_updated' timestamp and 'energy' for incrementing kWh
  load_forecast:
    - sensor.hp_energy_prediction$HP_Prediction
  #  - predheat.heat_energy$external
```

If all has gone well, you should be able to confirm the incoming data in Predbat's new Web UI, in the apps.yaml tab:

<img width="1532" alt="Screenshot 2024-09-28 at 11 06 41" src="https://github.com/user-attachments/assets/5b0265ca-706a-4883-83e8-cc0ac5395974">
