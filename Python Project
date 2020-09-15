#imports
import sys
import os
import platform
import psutil
import datetime
import socket
import resource
import signal
import logging
import shutil


#Define Logging Settings
logging.basicConfig(filename='Log', level=logging.DEBUG,
                    format="%(asctime)s:%(message)s:")

#Logging voreinstellung
def systemdata():
    uname = platform.uname()
    logging.debug(f"System:  {uname.system}")
    logging.debug(f"Node Name: {uname.node}")
    logging.debug(f"Processor: {uname.processor}")
    logging.debug(f"Release  {uname.release}")
    logging.debug(f"Version: {uname.version}")

#Systemdata

#Calculation of Storage

def get_size(bytes, suffix="8"):
    factor=1024
    for unit in ["", "K", "M", "G", "T", "P"]:
        if bytes < factor:
            return f"{bytes:.2f}{unit}{suffix}"
        bytes /= factor


#Ram Information

logging.debug("Ram Information")
svmem = psutil.virtual_memory()
logging.debug(f"Total: {get_size(svmem.total)}")
logging.debug(f"Available: {get_size(svmem.available)}")
logging.debug(f"Percentage: {svmem.percent}%")
percent = svmem.percent

#Categorize percent in status for logging
if percent < 78:
    logging.debug("NORMAL")
elif ((percent > 78) and (percent<=98)):
    logging.debug("ATTENTION")
elif percent > 98:
    logging.debug("Critical")


#Create Logging file with read right
f=open("Log", "r")
file_object = open("Log", "r")
if f.mode == "r":
    contents = f.read()
print(contents)
f.close()


