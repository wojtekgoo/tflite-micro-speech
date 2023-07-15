### How to Install

This code is specific for Nano 33 BLE Sense:
cd My Documents\Arduino\Libraries
git clone https://github.com/tensorflow/tflite-micro-arduino-examples Arduino_TensorFlowLite

To save some space:
rmdir docs
rmdir .git
rmdir .github

xcopy examples examples.bak /e /i /h

Open project:
File->Examples->Arduino_TensorFlowLite->micro_speech


git config --global user.name "wojtekgoo"
git config --global user.email .....@....

Create local repo:
git init
git add .
(git rm nazwa_pliku .)
git commit -m "Initial commit"
git status

Create tflite-micro-speech repo on Github

Add a remote repo:
git remote add origin https://github.com/wojtekgoo/tflite-micro-speech
(git remote rm origin)
git branch -M main   (if main is default branch, but git keeps committing to master)
git add .
git commit -m "Initial commit"
git push --set-upstream --force origin main

Authorize with browser
`~/Arduino/libraries` on Linux, `~/Documents/Arduino/libraries/` on MacOS, and
`My Documents\Arduino\Libraries` on Windows.

Once you're in that folder in the terminal, you can then grab the code using the
git command line tool:

```
git clone https://github.com/tensorflow/tflite-micro-arduino-examples Arduino_TensorFlowLite
```

To update your clone of the repository to the latest code, use the following terminal commands:
```
cd Arduino_TensorFlowLite
git pull
```

### Checking your Installation

Once the library has been installed, you should then start the Arduino IDE.
You will now see an `Arduino_TensorFlowLite`
entry in the `File -> Examples` menu of the Arduino IDE. This submenu contains a list
of sample projects you can try out.

![Hello World](docs/hello_world_screenshot.png)

## Compatibility

This library is designed for the `Arduino Nano 33 BLE Sense` board. The framework
code for running machine learning models should be compatible with most Arm Cortex
M-based boards, such as the `Raspberry Pi Pico`, but the code to access peripherals
like microphones, cameras, and accelerometers is specific to the `Nano 33 BLE Sense`.

## License

This code is made available under the Apache 2 license.