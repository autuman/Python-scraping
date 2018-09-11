# Python-scraping
Tips when scraping with python

1. Check browser header: 
 https://www.whatismybrowser.com/
 https://www.whatismybrowser.com/detect/what-http-headers-is-my-browser-sending
 
2. Edit cookis
 http://www.editthiscookie.com/
 
3. Behavior like a human: use time wait; avoid hidden input fields; avoid honeypots: use Selenium ele.is_dis
played() method

4. Use Selenium to load pages to scrape JS.

5. CAPTCHAs auto recognition

6. IP address anonymity:Tor + PySOCK

import socks

import socket 

from urllib.request import urlopen

socks.set_default_proxy(socks.SOCKS5, "localhost", 9150)

socket.socket = socks.socksocket

print(urlopen('http://icanhazip.com').read())


from selenium import webdriver

service_args = [ '--proxy=localhost:9150', '--proxy-type=socks5', ]

driver = webdriver.PhantomJS(executable_path='<path to PhantomJS>', service_args=service_args)
 
driver.get("http://icanhazip.com")

print(driver.page_source)

driver.close()
