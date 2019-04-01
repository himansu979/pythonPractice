#### to know the python version installed.
```
python
import cv2
cv2.__version__

pip freeze | findstr "opencv-python"
pip list | findstr "opencv-python"
pip show numpy | findstr "Version"

pip list --outdated
```
