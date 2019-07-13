# Wifi Connect via the Terminal

<br>

Author: Evan Sherwood
Github: Alanwatts42/Linux-dev-notes

<br>

- first, you can use `iwconfig` to figure out what your wireless card is called.

- The one on your laptop is wlp2s0 (I think) but double-check it anyway.

<br>

- Once you have the name of the wifi card in your computer, you should be able 
to scan with `sudo iwlist wlp2s0 scan` or more generically: 
`sudo iwlist <wificard-name> scan`

- This will let you figure out the SSID of the network you want to connect to.

<br>

- Once you have the SSID, you can use nmcli to connect to it. 

Here's how you do that:

```
nmci dev wifi connect <mySSID> password <myPassword>
```

<br>

This should work, so you should be connected. If not though, you should get some 
feedback text from the terminal after you tried this, so if you google that it 
should pull up the answer for you. Usually works for me anyway.
