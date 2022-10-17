# Tesla Charging AMPs enforcer

## Background / why this exists
When using level 1 charging and when using long (~ 50ft) extension cord, voltage sporadically oscillates.
As Tesla's "Smart" charger detects voltage drop it lowers AMPs that pull current thus lowering charging speed.

That behavior is annoying as it decreases charge speed.

## Approach
This script will poll car every 60 minutes and if AMPs currently used is lower than AMPs requested and Voltage is is not too low, it will restart charging.

## Usage
- `bundle` - install all dependencies
- `bundle exec ./bin/authenticate` - authenticate and store refresh token into MacOS keychain
- `bundle exec ./bin/monitor` - poll and restart charging when needed

## Script assumptions
* You are using MacOS
* You are using 125 volt based charging / level 1
* Tested on Ruby 2.6.8

# References
* https://github.com/haha150/tesla-api-server - sample authentication script
* https://github.com/timdorr/tesla-api - SDK to interface with Tesla


# Further improvements
* Explore / utilize [streaming](https://tesla-api.timdorr.com/vehicle/streaming) API to see if it could replace current polling implementation
