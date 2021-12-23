# LOGGING
Logging levels:
    debug -> info -> warning -> error -> critical

```
import logging

logger = logging.getLogger(__name__)
logger.setLevel(logging.INFO)

formmater = logging.Formatter("%(asctime)s %(levelname)s:%(message)s")

file_handler = logging.getFileHandler("logfile_path.log")
file_handler.setFormatter(formmater)

stream_handler = logging.getStreamHandler()

logger.add(file_handler)

logger.debug("Some logs here")1
```
___________________________________
# ITERATE THROUGH FOLDERS
```
import os
import os.path
from pathlib import Path
import shutil

paths = []
for dirpath, dirnames, filenames in os.walk("profile_pictures"):
    for filename in [f for f in filenames]:
```
___________
# CREATE CHROME DRIVER
```
import selenium
from selenium import webdriver

CHROME_PATH = r'/home/minhnd/Documents/baomoi/chromedriver_95'

driver = webdriver.Chrome(executable_path=CHROME_PATH)
```
