## Arduino TensorFlow Lite micro-speech project

TODO: desc

## Project setup

On Windows
```
cd My Documents\Arduino\Libraries
git clone https://github.com/tensorflow/tflite-micro-arduino-examples Arduino_TensorFlowLite
rmdir docs
rmdir .git
rmdir .github
xcopy examples examples.bak /e /i /h
```

Open project in Arduino: `File->Examples->Arduino_TensorFlowLite->micro_speech`

Config git
```
git config --global user.name "wojtekgoo"
git config --global user.email .....@....
```

Create local repo
```
git init
git add .
(git rm nazwa_pliku .)
git commit -m "Initial commit"
git status
```

Create tflite-micro-speech repo on Github

Add a remote repo
```
git remote add origin https://github.com/wojtekgoo/tflite-micro-speech
(git remote rm origin)
git branch -M main   (if main is default branch, but git keeps committing to master)
git add .
git commit -m "Initial commit"
git push --set-upstream --force origin main
```

Authorize with browser
Make changes
`git push origin`


## Compatibility

This library is designed for the `Arduino Nano 33 BLE Sense` board. The framework
code for running machine learning models should be compatible with most Arm Cortex
M-based boards, such as the `Raspberry Pi Pico`, but the code to access peripherals
like microphones, cameras, and accelerometers is specific to the `Nano 33 BLE Sense`.

## License

This code is made available under the Apache 2 license.