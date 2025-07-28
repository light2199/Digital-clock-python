# Digital-clock-python

from PyQt5.QtWidgets import  QWidget,QApplication,QLabel,QVBoxLayout

import sys

from PyQt5.QtCore import Qt, QTimer, QTime

from PyQt5.QtGui  import QIcon


class DigitalClock(QWidget):
    def __init__(self):
        super().__init__()

        self.timelabel=QLabel("12:00:00",self)
        self.timer=QTimer(self)
        self.setWindowIcon(QIcon("clockimah=ge.jpg"))
        self.initUI()

    def initUI(self):
        self.setWindowTitle("DIGITAL CLOCK")
        self.setGeometry(500,500,400,200)


        vbox=QVBoxLayout()
        vbox.addWidget(self.timelabel)
        self.setLayout(vbox)

        self.timelabel.setAlignment(Qt.AlignCenter)

        self.timelabel.setStyleSheet("font-size:70px;"
                                    "font-family:Arial;"
                                    "color:Green;")
        self.setStyleSheet("background-color: black;")

        self.update_time()


        self.timer.timeout.connect(self.update_time)
        self.timer.start(1000)

        



    def update_time(self):
        current_time=QTime.currentTime().toString("hh:mm:ss AP")
        self.timelabel.setText(current_time)

        







if __name__=="__main__":
    app=QApplication([])
    digital_clock=DigitalClock()
    digital_clock.show()
    sys.exit(app.exec_())
