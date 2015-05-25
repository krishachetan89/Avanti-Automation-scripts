# -*- coding: utf-8 -*-
# Copyright 2015 kc@ibtechnology

import unittest
import os
import time
from random import randint
from appium import webdriver
from time import sleep

from selenium.webdriver.common.keys import Keys

class AvantiIOSTests(unittest.TestCase):

    def setUp(self):
        # set up appium
        #Specify path to app, app and code should be in same location
        app = os.path.join(os.path.dirname(__file__),
                           '/Volumes/Mobility/Avanti/Avanti Market.ipa')
        app = os.path.abspath(app)
        self.driver = webdriver.Remote(
            command_executor='http://127.0.0.1:4723/wd/hub',
            desired_capabilities={
                'app': 'com.byndl.AvantiMarket',  # App name
                'deviceName': "iPhone 6",  # Specify Phone name here
                'platformName': 'iOS',  # Specify Platform name here
                'platformVersion': '8.1',  # Specify iOS version here
                'udid': '0387fd7fa500c34cc3ccdc80453bfa5d722bb048'  # Specify device udid here

            })

    def tearDown(self):
        self.driver.quit()

    def test_login(self):
# wait for login screen to appear
        self.driver.implicitly_wait('20')
        print('Trying to login with indiaone@avantilab.org')
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIATextField[1]').send_keys('indiaone@avantilab.org')
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIASecureTextField[1]').send_keys('12345678')
        self.driver.hide_keyboard()
        self.driver.implicitly_wait(10)
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIAButton[3]').click()
        time.sleep(20)
        self.driver.implicitly_wait(99)
        try:
            self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIASecureTextField[1]')
        except :
            print('Login failed, please check credentials and network')
        else:
            print('Login successful, creating pin')

        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIASecureTextField[1]').send_keys('1')
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIASecureTextField[2]').send_keys('1')
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIASecureTextField[3]').send_keys('1')
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIASecureTextField[4]').send_keys('1')
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIASecureTextField[5]').send_keys('1')
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIASecureTextField[6]').send_keys('1')
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIASecureTextField[7]').send_keys('1')
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIASecureTextField[8]').send_keys('1')

        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIAButton[1]').click()
        self.driver.implicitly_wait(10)
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[5]/UIAAlert[1]/UIACollectionView[1]/UIACollectionCell[1]/UIAButton[1]').click()
        self.driver.implicitly_wait(10)
        try:
            self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIAButton[1]')
        except  :
            print('Unable to create pin, please enter pin properly')

        else:
            print('Pin created successfully')
# Navigating to pay screen
        print('Navigating to pay screen')
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIAButton[1]').click()
        self.driver.implicitly_wait(10)
# Swiping through the cards

        for x in range(0, 3):
            self.driver.swipe(start_x=300, start_y=281, end_x=75, end_y=281, duration=500)
            self.driver.implicitly_wait(10)
            self.driver.swipe(start_x=75, start_y=281, end_x=300, end_y=281, duration=500)

        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIAButton[1]').click()
        self.driver.implicitly_wait(10)
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIAButton[1]').click()
        self.driver.implicitly_wait(10)
# Reloading from pay screen
        print('Navigating to reload screen from pay screen')
        try:
            self.driver.find_element_by_name('RELOAD').click()
            self.driver.implicitly_wait(10)
        except:
            print('Unable to find reload button')
        else:
            print('Trying to reload 10$')
        try:
            self.driver.find_element_by_name('$10').click()
        except :
            print('Specified amount of 10$  amount not found')
        else:

            self.driver.implicitly_wait(10)
#selecting the first card from available cards
        print('selecting the first card from available cards')
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIATableView[2]/UIATableCell[1]').click()
        self.driver.implicitly_wait(10)
        self.driver.find_element_by_name('CONFIRM').click()
        self.driver.implicitly_wait(10)
        try:
            self.driver.find_element_by_name('OK').click()
        except :
            print('Reload failed')
        else:
            print('Reload successful')
            self.driver.implicitly_wait(10)
        print('Trying to update info')
        try:
            self.driver.find_element_by_name('UPDATE INFO').click()
            self.driver.implicitly_wait(10)
        except:
            print('Update info not find')
        else:
            self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIATextField[1]').send_keys('Bangalore')
            self.driver.implicitly_wait(10)
        self.driver.find_element_by_name('Return').click()
        self.driver.implicitly_wait(10)
        self.driver.find_element_by_name('DONE').click()
        self.driver.implicitly_wait(10)
        print('card renamed successfully')
        try:
            self.driver.find_element_by_name('OK').click()
        except:
            print('Unable to change name of card')
        else:

            self.driver.implicitly_wait(10)
            self.driver.find_element_by_name('SideMenu').click()
        self.driver.implicitly_wait(99)
        self.driver.find_element_by_name('WAYS TO PAY').click()
        self.driver.implicitly_wait(10)

# Swiping through the cards

        for x in range(0, 3):
            self.driver.swipe(start_x=300, start_y=281, end_x=75, end_y=281, duration=500)
            self.driver.implicitly_wait(10)
            self.driver.swipe(start_x=75, start_y=281, end_x=300, end_y=281, duration=500)
        print('Trying to update info of card')
        try:
            self.driver.find_element_by_name('UPDATE INFO').click()
            self.driver.implicitly_wait(10)
        except:
            print('Update info failed')
        else:
            self.driver.find_element_by_name('DONE').click()
            self.driver.implicitly_wait(10)
        self.driver.find_element_by_name('UPDATE').click()
        self.driver.implicitly_wait(10)
        try:
            self.driver.find_element_by_name('OK').click()
        except:
            print('Unable to update card')
        else:
            print('Card updated successfully')

        self.driver.implicitly_wait(10)
        self.driver.find_element_by_name('SideMenu').click()
        self.driver.implicitly_wait(10)
        print('Navigating to support')
        try:
            self.driver.find_element_by_name('SUPPORT').click()
            self.driver.implicitly_wait(10)
        except:
            print('Unable to navigate to support')
        finally:
            print("Navigating to Helpful how to's")
        try:

            self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIAButton[1]').click()
            self.driver.implicitly_wait(10)
        except :
            print("Helpful how to's not present")
        finally:
            print('Navigating to Set up a My MarketCard account ')
            self.driver.find_element_by_name('Using The Market').click()
            self.driver.implicitly_wait(10)
            self.driver.find_element_by_name('Set up a My MarketCard account').click()
            self.driver.implicitly_wait(10)
# Play video from Set up a My MarketCard account
            self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIAScrollView[1]/UIAWebView[1]').click()
            time.sleep(7)
        for x in range(0, 3):
            self.driver.find_element_by_name('backButton').click()
        self.driver.implicitly_wait(5)
# support screen
        print('Navigating to support screen')
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIAButton[2]').click()
        self.driver.implicitly_wait(10)
        self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIAButton[5]').click()
        self.driver.implicitly_wait(10)
        print('Selecting purchase issue from list')
        try:
            self.driver.find_element_by_name('Purchase Issue').click()
            self.driver.implicitly_wait(10)
        except:
            print('Unable to select purchase issue')
        else:
            self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIAButton[6]').click()
            self.driver.implicitly_wait(10)
        print('Selecting kiosk scans the wrong item')
        try:

            self.driver.find_element_by_name("Kiosk scans the wrong item").click()
            self.driver.implicitly_wait(10)
        except:
            print('Unable to select Kiosk scans the wrong item')
        else:
            print('Sending text into text box')
            self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIATextView[1]').send_keys("Hi Team,thank you :)")

        self.driver.implicitly_wait(10)
        self.driver.find_element_by_name('Return').click()
        self.driver.implicitly_wait(10)
        print('Selecting next')
        try:
            self.driver.find_element_by_name('NEXT').click()
            self.driver.implicitly_wait(10)
        except:
            print(' Unable to find next button')
        else:
            self.driver.find_element_by_name('OR SEND REQUEST').click()
            self.driver.implicitly_wait(10)
        self.driver.find_element_by_name('backButton').click()
        self.driver.implicitly_wait(10)
        self.driver.find_element_by_name('SideMenu').click()

        print('Trying to sign out')
        try:
            self.driver.implicitly_wait(10)
            self.driver.find_element_by_name('SIGN OUT').click()
            self.driver.implicitly_wait(10)
        except:
            print('Sign out button not found')
        else:
            print('Tapping on sign out')
            self.driver.implicitly_wait(10)
        try:
            self.driver.implicitly_wait(10)
            self.driver.find_element_by_xpath('//UIAApplication[1]/UIAWindow[2]/UIATextField[1]')
        except:
            print('Sign out unsuccessful')
        else:
            print('Sign out successful')




if __name__ == '__main__':
    suite = unittest.TestLoader().loadTestsFromTestCase(AvantiIOSTests)
    unittest.TextTestRunner(verbosity=2).run(suite)
