# ecobee
A command line tool to control a Ecobee thermostat

This code was based off of an existing project that, I sadly, can't recall.

The code can be run on a command line or automated to be called from a crontab.

You can set the temperature, fan, humidity, clear hold, etc. It can easily be extended to the other APIs that ecobee supports.

The status output is shown as below - which includes the weather forecast:

    >ecobee       
    Thermostat name:            Home
      ID:                       1
      Current climate ref:      sleep
      Equipment running:        fan
      Update time:              2017-11-30 03:01:20
      Update time:              2017-11-30 03:01:20
      Temperature actual:       19.50 C
      Temperature set:          19.00 C
      Fan:                      on
      Humidity:                 43 %
      Humidity adjusted:        44 %
        Mode:                   manual
          Setpoint (set):       50 %
      Sensor spread             1.33 C
      HVAC mode:                heat
      Follow me:                False
      Sensor: Upstairs(In Use)
        Temperature:            20.17 C
        Occupied:               true
      Sensor: Home(In Use)
        Temperature:            18.83 C
        Humidity:               43
        Occupied:               true
      Heat 2-stage differential:2.78 C
      Event:                    hold
        Running:                True
        Fan:                    on
        Start:                  2017-11-25 23:10:42
        End:                    2035-01-01 00:00:00
      Forecasts:             ETA(Hours)    Temp/Hum/AdjHum    High/   Low
        2017-11-29 21:27:08    -0.6       -3.44/ 71/ 17    /  3.39/ -6.00
        2017-11-30 21:27:08    23.4       -1.33/ 80/ 22    /  3.39/ -6.00
        2017-12-01 21:27:08    47.4       -0.28/ 73/ 21    /  2.78/ -3.33
        2017-12-02 21:27:08    71.4       -1.06/ 79/ 22    /  2.00/ -4.11
        2017-12-03 21:27:08    95.4        1.89/ 82/ 28    /  5.00/ -1.22
        2017-11-30 00:00:00     2.0       -5.61/ 81/ 17    
        2017-11-30 06:00:00     8.0       -6.00/ 89/ 18    
        2017-11-30 12:00:00    14.0        3.39/ 76/ 28    
        2017-11-30 18:00:00    20.0        3.39/ 91/ 34    

Here is the help API

    >ecobee --help
    usage: ecobee [-h] [--verbose] [--temperature TEMPERATUREHOLD] [--fan]
                  [--auto AUTOTHRESHOLD] [--humidity HUMIDITYLEVEL]
                  [--humidifier-mode HUMIDIFIERMODE]
                  [--stage1HeatingDifferentialTemp STAGE1HEATINGDIFFERENTIALTEMP]
                  [--fahrenheit] [--clear] [--name NAME] [--status] [--dump]
    
    Interface to Ecobee thermostat.
    
    optional arguments:
      -h, --help            show this help message and exit
      --verbose, -v         Verbose
      --temperature TEMPERATUREHOLD, -t TEMPERATUREHOLD
                            Set a temperature hold.
      --fan, -f             Set fan hold
      --auto AUTOTHRESHOLD, -a AUTOTHRESHOLD
                            Set a temperature differential between the sensors to
                            automically turn on or off the fan.
      --humidity HUMIDITYLEVEL, -hum HUMIDITYLEVEL
                            Set the desired relative humidity level in percent.
      --humidifier-mode HUMIDIFIERMODE, -hm HUMIDIFIERMODE
                            Humidifier mode (auto,off,manual)
      --stage1HeatingDifferentialTemp STAGE1HEATINGDIFFERENTIALTEMP
                            stage1HeatingDifferentialTemp
      --fahrenheit, -fah    Use Fahrenheit instead of Celcius for temperatures
      --clear, -c           Clear all holds
      --name NAME, -n NAME  Thermostat name. Default will be the first one found -
                            which is OK if you only have one thermostat.
      --status, -s          Get the status
      --dump, -d            Dump everything
