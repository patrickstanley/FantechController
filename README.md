# FantechControl
Reverse engineer and duplicate Fantech ERV controls for improved home automation

## Background:
I bought a [Fantech 200E Energy Recovery Ventilator](https://shop.fantech.net/en-US/atmo200e--fresh--air--appliance/p747374) for use in my home. The only control options for it are to use their own [custom controllers](https://shop.fantech.net/en-US/eco--touch--auto--iaq--control/p500853), which allow for speed selecting and fine tuning using the electronically controlled motors (ECM), or to just put a dry contact across D+ and D- to turn it on and off. 

For the time being, and to get the HVAC project done, I bit the bullet and bought the controller. But now I want to better integrate the system into Home Assistant. The first step is to determine what the communications method is between the controller and the ERV, so that I can duplicate commands sent between.

This repo is largely a work in progress and a place for me to store things as I work. I found several people who had alluded to having the info to bit bang things between the controller and the ERV but no details given. So I am going to work out in the open incase anyone else wants to join or has details to share.

## Communications Protocol:
Using a [cheap logic analyzer](https://www.amazon.com/dp/B077LSG5P2?psc=1&ref=ppx_yo2ov_dt_b_product_details) and [PulseView](https://sigrok.org/wiki/PulseView) I was able to determine that the system used MODBUS RTU over RS-485 at 9600 baud for comms. Dumps of the intial logic analyzer data are included. This conclusion was also supported by the fact that the comms wires are labeled A and B, which are common RS-485 labels. D+ provides ~13V, and ground is the arrow pointing down.

Next step is to determine the imporant registers and device ID's.