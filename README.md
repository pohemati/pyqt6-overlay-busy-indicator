
# PyQt6 Overlay Busy Indicator

A customizable overlay busy indicator with a smooth fade animation for PyQt6

If you are using PySide6, you can download the code in [PySide6](https://github.com/pohemati/pyside6-overlay-busy-indicator).


## Installation

Install package using pip

```python
  pip install pyqt6-overlay-busy-indicator
```



## Screenshots

![App Screenshot](https://raw.githubusercontent.com/pohemati/pyqt6-overlay-busy-indicator/main/qbusyindicator/assets/screenshot.gif)



## Usage/Examples

```python
from qbusyindicator import QOverlayBusyIndicator


class Dialog(QtWidgets.QDialog):
    def __init__(self, parent=None):
        super().__init__(parent)
        # widgets and layouts
        self.busy_indicator = QOverlayBusyIndicator(self)
        
        # connecting signals
        self.busy_indicator.started.connect(lambda: print('started'))
        self.busy_indicator.stopped.connect(lambda: print('stopped'))

        # start the indicator
        self.busy_indicator.start()
        
        # stop the indicator
        self.busy_indicator.stop()

        # stop the indicator after 5 seconds
        self.busy_indicator.stopAfter(5000)

        # returns True if the indicator is currently busy
        self.busy_indicator.isBusy() 

        # returns True if the indicator is about to stop(e.g. returns true after calling stopAfter method)
        self.busy_indicator.isStopping()

        # returns True if the indicator is currently stopped
        self.busy_indicator.isStopped()

        # sets the busy gif animation/image path
        # you can use qt resources files too
        # for clearing image/gif animation you can call this method using an empty string
        self.busy_indicator.setImagePath('loading.gif') 

        # returns gif animation path
        self.busy_indicator.imagePath()

        # blocks keyboard input on dialog/window while busy. default is False
        self.busy_indicator.setBlockKeyboard(True) 

        # returns True if the keyboard input is blocked
        self.busy_indicator.keyboardBlocked()

        # blocks mouse input on dialog/window while busy. default is False
        self.busy_indicator.setBlockMouse(True) 

        # returns True if the mouse input is blocked
        self.busy_indicator.mouseBlocked()

        # sets the duration of fade in/out animations to 2 seconds. default is 400 msecs
        self.busy_indicator.setFadeDuration(2000) 

        # returns current fade duration
        self.busy_indicator.fadeDuratrion()

        # changing the label font
        self.busy_indicator.setLabelFont(QtGui.QFont('Calibri', 20))

        # returns current label font
        self.busy_indicator.labelFont()

        # changing the label text
        self.busy_indicator.setLabelText(self.tr('Loading...')) 

        # returns current label text
        self.busy_indicator.labelText()

        # changing the background color of overlay
        # default is rgba(204, 204, 204, 70)
        self.busy_indicator.setStyleSheet('background-color: rgba(204, 204, 204, 60);')
        
        # changing the color and style of the text
        # default is 'color: #808080; padding-top: 5px;'
        self.busy_indicator.label.setStyleSheet('color: #CCC; padding-top: 10px;')

    # never forget to override resizeEvent method of your dialog/window
    # to ensure that busy indicator will be automically resized with dialog
    def resizeEvent(self, event):
        self.busy_indicator.resize(event.size())
        return super().resizeEvent(event)
```

if you prefer snake-case syntax over camel-case, and you would like to use properties to access/customize widget's behavior you can use following example.

```python
from qbusyindicator import QOverlayBusyIndicator


class Dialog(QtWidgets.QDialog):
    def __init__(self, parent=None):
        super().__init__(parent)
        # widgets and layouts
        self.busy_indicator = QOverlayBusyIndicator(self)
        
        # connecting signals
        self.busy_indicator.started.connect(lambda: print('started'))
        self.busy_indicator.stopped.connect(lambda: print('stopped'))

        # start the indicator
        self.busy_indicator.start()
        
        # stop the indicator
        self.busy_indicator.stop()

        # stop the indicator after 5 seconds
        self.busy_indicator.stop_after(5000)

        # returns true if the indicator is currently busy
        self.busy_indicator.is_busy() 

        # returns true if the indicator is about to stop(e.g. returns true after calling stop_after method)
        self.busy_indicator.is_stopping()

        # returns true if the indicator is currently stopped
        self.busy_indicator.is_stopped()

        # sets the busy gif animation/image path
        # you can use qt resources files too
        # for clearing gif animation/image you can assign this attribute an empty string
        self.busy_indicator.image_path = 'loading.gif'

        # blocks keyboard input on dialog/window while busy. default is False
        self.busy_indicator.block_keyboard = True

        # blocks mouse input on dialog/window while busy. default is False
        self.busy_indicator.block_mouse = True

        # sets the duration of fade in/out animations to 2 seconds. default is 400 msecs
        self.busy_indicator.fade_duration = 2000

        # changing the label font
        self.busy_indicator.label_font = QtGui.QFont('Calibri', 20)

        # changing the label text
        self.busy_indicator.label_text = self.tr('Loading...')
    
    # never forget to override resizeEvent method of your dialog/window
    # to ensure that busy indicator will be automically resized with dialog
    def resizeEvent(self, event):
        self.busy_indicator.resize(event.size())
        return super().resizeEvent(event)
```


## Demo

After installing qbusyindicator package using pip, you can run demo.py file in the examples directory, for example:

```
cd examples
python demo.py
```

![Demo Screenshot](https://raw.githubusercontent.com/pohemati/pyqt6-overlay-busy-indicator/main/qbusyindicator/assets/demo-screenshot.png)
