# LumeAir Home Support

Need help with your LumeAir sensor or the LumeAir Home app? Start with the answers below. If they don't solve it, [email us](#contact).

## Setting up a sensor

To set up a new sensor, open LumeAir Home, choose **Set up a new sensor**, and follow the steps. Keep your phone close to the sensor, and have your Wi-Fi password ready.

### The app can't find my sensor

- Make sure the sensor is plugged in, and keep your phone within a few meters of it.
- Check that Bluetooth is on, and that LumeAir Home is allowed to use it (on Android, the **Nearby devices** permission).
- A sensor that's already on Wi-Fi only shows up for **2 minutes after it restarts**. Unplug it for a few seconds, plug it back in, then tap **Scan again**.

### My Wi-Fi network isn't in the list

- LumeAir sensors use **2.4 GHz Wi-Fi**. Most home routers offer it alongside 5 GHz, sometimes under a separate network name. A 5 GHz-only network won't appear.
- Move the sensor closer to your router while you set it up.
- You can also choose **Other network** and type the network name yourself.

### "That password didn't work"

Wi-Fi passwords are case-sensitive. Tap **Re-enter password**, check it, and try again. Using the wrong password doesn't cause any problems; you can retry straight away.

### "This sensor is already set up with another phone"

Each sensor accepts changes only from a phone that holds its access key. To use it from a second phone, either:

- **Share it:** on the first phone, go to **Settings › Sensors**, open the sensor's menu, and choose **Share pair code**. On the new phone, choose **Add a sensor already on Wi-Fi** and scan the code. Share the code only with people you trust: it gives full access to the sensor.
- **Start over:** factory reset the sensor (see below), then set it up again on the new phone.

## Readings

### A room says "offline" or "Cannot reach sensor"

- Your phone must be on the **same Wi-Fi network** as the sensor. LumeAir Home reads your sensors directly over your home network, so it can't reach them over mobile data or from outside your home.
- Check that the sensor is plugged in.
- Guest networks often stop devices from seeing each other. Keep your phone and sensors on your main network.
- If your router gives the sensor a new address, the app finds it again by itself. Give it a minute.

### When do readings appear, and how often do they update?

| Reading | First reading after the sensor starts | Then updates |
|---|---|---|
| Temperature and humidity | Straight away | Every 30 seconds |
| CO₂ | About 30 seconds | About every 30 seconds |
| PM2.5 and PM10 | About 1½ minutes | Every 5 minutes |
| VOC index | A few minutes | Every second |

The particle sensor rests between readings to make its fan and laser last longer, which is why PM2.5 and PM10 update every 5 minutes.

### The VOC index seems off

The VOC index compares the air with what's normal for that room, where about **100 is normal**. It learns the room over its first few hours, so readings settle down after that. It starts learning again whenever the sensor restarts.

### What do the colors mean?

In the app, go to **Settings › What the colors mean**. Particle ratings follow the US EPA Air Quality Index. Readings are informational and are not medical advice.

## Alerts and notifications

- Turn alerts on in **Settings › Alerts**, then set up **Phone notifications** with ntfy (free) or Pushover. Without one of them, alerts are only listed in each room's alert history.
- Your sensors send the alerts themselves, so they arrive even when LumeAir Home is closed. The sensor needs a working internet connection to send them.
- No alerts arrive during **quiet hours**. If a reading is still high when quiet hours end, you get the alert then.
- After setting up ntfy or Pushover, use the test notification to check that alerts reach your phone.

## Home Assistant

Your sensors can show up in Home Assistant 2026.3 or later, with every reading, an overall air-quality rating, and their alerts. Home Assistant reads each sensor directly on your home network.

1. In the app, go to **Settings › Home Assistant** and tap **Open in Home Assistant**. Download LumeAir from your Home Assistant's Marketplace, then restart Home Assistant.
2. Home Assistant finds your sensors by itself. In **Settings › Devices & services**, tap **Add** next to each LumeAir sensor.
3. Paste the sensor's pair code: in the app's **Settings › Home Assistant**, tap **Copy pair code** next to the sensor.

If you set a sensor up again later, Home Assistant asks for its new pair code. Full instructions are on the [LumeAir for Home Assistant](https://github.com/KyleBcine/lumeair-homeassistant#readme) page.

## Factory reset

A factory reset erases the sensor's Wi-Fi details, access key, alert settings and stored readings. You'll need to set it up again afterwards.

- **From the app:** go to **Settings › Sensors**, open the sensor's menu, and choose **Factory reset…**.
- **On the sensor:** hold its **BOOT** button for **10 seconds**. The light starts blinking after 3 seconds; keep holding. Letting go early erases nothing.

## Finding your versions

When you contact us, it helps to include:

- **App version:** **Settings**, at the bottom, under About.
- **Sensor firmware version:** **Settings › Sensors**, shown under each sensor.

## Contact

Email [lumeair.home@gmail.com](mailto:lumeair.home@gmail.com). Tell us what happened, what you expected, and your app and firmware versions.

For how we handle your information, see our [Privacy policy](Privacy).
