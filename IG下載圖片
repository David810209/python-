#log in ig,search the keyword and download the picture
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.common.keys import Keys
import time
import os
import wget
#connect to the IG web
PATH = "D:/users/user/Desktop/chromedriver.exe"
driver = webdriver.Chrome(PATH)
driver.get("https://www.instagram.com/")
#log in IG
username = WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.NAME, "username"))
)
password = WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.NAME, "password"))
)
login = driver.find_element_by_xpath('//*[@id="loginForm"]/div/div[3]')

username.clear()
password.clear()
#input 帳密 there
username.send_keys('')
password.send_keys('')
login.click()

#input keyword and search
search = WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.XPATH, '//*[@id="react-root"]/section/nav/div[2]/div/div/div[2]/input'))
)
keyword = "#菸蒂觀察"#input keyword there
search.send_keys(keyword)
time.sleep(1)
search.send_keys(Keys.RETURN)
time.sleep(1)
search.send_keys(Keys.RETURN)
#find picture's className on HTML
WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.CLASS_NAME, "FFVAD"))
)

for i in range(5):
    driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
    time.sleep(5)
imgs = driver.find_elements_by_class_name("FFVAD")

path = os.path.join(keyword)
os.mkdir(path)
#download
count = 0
for img in imgs:
    save_as = os.path.join(path, keyword + str(count) + '.jpg')
    wget.download(img.get_attribute("src"), save_as)
    count += 1
