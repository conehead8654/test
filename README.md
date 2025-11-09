Xvfb :1 -screen 0 1024x768x24 & export DISPLAY=:1 && fluxbox &
websockify --web=/usr/share/novnc 6080 localhost:5900






# Install the necessary graphical dependencies
sudo apt-get update -y
sudo apt-get install -y xvfb x11vnc fluxbox websockify novnc firefox
# Start the virtual display and desktop manager
Xvfb :1 -screen 0 1024x768x24 & export DISPLAY=:1
fluxbox &
# Start the VNC server and stream to your browser on port 6080
x11vnc -display :1 -nopw -forever -shared -rfbport 5900 &
websockify --web=/usr/share/novnc 6080 localhost:5900
