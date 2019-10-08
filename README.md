# fusuma_mint_xfce
Fusuma Linux Mint XFCE mutlitouch gestures





## How to install FUSUMA

### 1. Grant permission to read the touchpad device
**IMPORTANT**: You **MUST** be a member of the **INPUT** group to read touchpad by Fusuma.

```bash
$ sudo gpasswd -a $USER input
```

Then, You **MUST** **LOGOUT/LOGIN or REBOOT** to assign this group.

### 2. Install libinput-tools
You need `libinput` release 1.0 or later.

```bash
$ sudo apt-get install libinput-tools
```

### 3. Install xdotool for custom Linux Mint XFCE gestures

For sending shortcuts:
```bash
$ sudo apt-get install xdotool
```

### 4. Install Ruby
Fusuma runs in Ruby, so you must install it first.

```bash
$ sudo apt-get install ruby
```

### 5. Install Fusuma

```bash
$ sudo gem install fusuma
```



### Touchpad not working in GNOME

Ensure the touchpad events are being sent to the GNOME desktop by running the following command:


```bash
$ gsettings set org.gnome.desktop.peripherals.touchpad send-events enabled
```

## Usage

```bash
$ fusuma
```

## Update

```bash
$ sudo gem update fusuma
```

## Customize Gesture Mapping

You can customize the settings for gestures to put and edit `~/.config/fusuma/config.yml`.
**NOTE: You will need to create the `~/.config/fusuma` directory if it doesn't exist yet.**

```bash
$ mkdir -p ~/.config/fusuma        # create config directory
$ nano ~/.config/fusuma/config.yml # edit config file.
```

### Example 1: Gesture Mapping for elementary OS

```yaml
swipe:
  3:
    left:
      command: 'xdotool key alt+Left'
    right:
      command: 'xdotool key alt+Right'
    up:
      command: 'xdotool key ctrl+t'
      threshold: 1.5
    down:
      command: 'xdotool key ctrl+w'
      threshold: 1.5
  4:
    left:
      command: 'xdotool key super+Left'
    right:
      command: 'xdotool key super+Right'
    up:
      command: 'xdotool key super+a'
    down:
      command: 'xdotool key super+s'
pinch:
  2:
    in:
      command: 'xdotool key ctrl+plus'
      threshold: 0.1
    out:
      command: 'xdotool key ctrl+minus'
      threshold: 0.1

threshold:
  swipe: 1
  pinch: 1

interval:
  swipe: 1
  pinch: 1
```