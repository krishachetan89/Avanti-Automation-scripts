#-*- coding: utf-8 -*-
__author__ = 'chetan.krishna'
import os
import time
import unittest
from time import sleep
from appium import webdriver
from pylab import *


# Returns absolute path relative to this file
PATH = lambda p: os.path.abspath(
    os.path.join(os.path.dirname(__file__), p)
)


class AvavntiAndroidTests(unittest.TestCase):
    def setUp(self):
        desired_caps = {}
# Specify platform below(Android, iOS)
        desired_caps['platformName'] = 'Android'
# Specify OS version(Settings->About phone -> android version)
        desired_caps['platformVersion'] = '4.4.4'
# Obtain the Device name from Adb[For Android](Terminal Command: "adb devices")
        desired_caps['deviceName'] = '9e3484f6'

        desired_caps['noReset'] = False
# Specify the path to Application
        desired_caps['app'] = PATH('AvantiMarket.apk')
# Wait for email login activity to appear
        desired_caps["appWaitActivity"]= ('com.android.avantimarket.ui.activity.EmailLoginActivity')
        self.driver = webdriver.Remote('http://localhost:4723/wd/hub', desired_caps)

    def tearDown(self):
# end the session
        self.driver.quit()


    def test_Avanti(self):
# wait for the login screen to appear
        self.driver.implicitly_wait(20)
# set values for plotting pass and fail results
        nPass = 0
        nFail = 0
        print('Checking login for registered user')
# logging in as indiaone@avantilab.org
        self.driver.find_element_by_id('com.android.avantimarket:id/m_emailTextField').send_keys('indiaone@avantilab.org')
        nPass= nPass+1
        self.driver.implicitly_wait(20)
        self.driver.find_element_by_id('com.android.avantimarket:id/m_passwordTextField').send_keys('12345678')
        nPass= nPass+1
        self.driver.back()
        self.driver.implicitly_wait(10)
        self.driver.find_element_by_name('SIGN IN').click()
        self.driver.implicitly_wait(30)
        time.sleep(10)
# validating for successful login
        try:
            self.driver.find_element_by_id('com.android.avantimarket:id/m_pinDigitOneTextField')
            print('Login successful')
            nPass= nPass+1
        except:
            print('Login failed')
            nFail = nFail + 1
        else:
# Creating pin required for login
            print('Creating Pin for user')
        self.driver.find_element_by_id('com.android.avantimarket:id/m_pinDigitOneTextField').send_keys('1')
        self.driver.find_element_by_id('com.android.avantimarket:id/m_pinDigitTwoTextField').send_keys('1')
        self.driver.find_element_by_id('com.android.avantimarket:id/m_pinDigitThreeTextField').send_keys('1')
        self.driver.find_element_by_id('com.android.avantimarket:id/m_pinDigitFourTextField').send_keys('1')
        self.driver.find_element_by_id('com.android.avantimarket:id/m_re_pinDigitOneTextField').send_keys('1')
        self.driver.find_element_by_id('com.android.avantimarket:id/m_re_pinDigitTwoTextField').send_keys('1')
        self.driver.find_element_by_id('com.android.avantimarket:id/m_re_pinDigitThreeTextField').send_keys('1')
        self.driver.find_element_by_id('com.android.avantimarket:id/m_re_pinDigitFourTextField').send_keys('1')
        self.driver.implicitly_wait(20)
        self.driver.find_element_by_id('com.android.avantimarket:id/m_saveButton').click()
        self.driver.implicitly_wait(10)
        self.driver.find_element_by_id('com.android.avantimarket:id/btn_cominsoon_Yes').click()
        self.driver.implicitly_wait(10)
# Checking for successful pin creation
        try:
            self.driver.find_element_by_id('com.android.avantimarket:id/m_balanceButton')
            print('Pin login successful')
            nPass=nPass+1
        except:
             print('Pin login is delayed, check your network')
             nFail = nFail+1
# Navigating to pay screen
        finally:
            time.sleep(5)
            print('Attempting to navigate to pay screen')
            self.driver.find_element_by_id('com.android.avantimarket:id/m_balanceButton').click()
            self.driver.implicitly_wait(10)
        print('Swiping between cards')
# Swiping between cards
        try:
            for x in range(0, 5):
                self.driver.swipe(start_x=950,start_y=780,end_x=150,end_y=780)
                self.driver.implicitly_wait(5)
                self.driver.swipe(start_x=150,start_y=780,end_x=950,end_y=780)
        except:
            print('Swiping cards failed')
            nFail = nFail+1
        finally:
            print('Cards swiped successfully')
            nPass= nPass+1
        print('Navigating to pay screen')
        self.driver.find_element_by_id('com.android.avantimarket:id/m_payButton').click()
        self.driver.implicitly_wait(10)
        try:
            self.driver.implicitly_wait(10)
            self.driver.find_element_by_id('com.android.avantimarket:id/m_doneButton')
            print('Successfully navigated to pay screen')
            nPass= nPass+1
        except:
            print('Navigating to Pay screen failed')
            nFail = nFail + 1

        else:
            self.driver.find_element_by_id('com.android.avantimarket:id/m_doneButton').click()
            self.driver.implicitly_wait(10)

# Trying to reload
        try:
            self.driver.find_element_by_id('com.android.avantimarket:id/m_reloadButton').click()
            self.driver.implicitly_wait(10)
        except:
            print('Reload Failed,Cannot reload')
            nFail = nFail+1
        else:
            nPass=nPass+1
            print('Attempting to reload with 10$')
            self.driver.find_element_by_id('com.android.avantimarket:id/m_tenCheckbox').click()
            self.driver.implicitly_wait(10)
        print('Selecting first card from available cards')
        try:
            self.driver.find_element_by_id('com.android.avantimarket:id/m_firstCardNumber').click()
            self.driver.implicitly_wait(10)
        except:
            print(' No card present')
            nFail = nFail+1
        finally:
            print('Successfully selected first card')
            nPass=nPass+1
        self.driver.find_element_by_id('com.android.avantimarket:id/m_confirmButton').click()
        self.driver.implicitly_wait(10)
        try:
            self.driver.find_element_by_name('OK').click()
            self.driver.implicitly_wait(10)
            print('Successfully reloaded your card with 10$')
            nPass= nPass+1
        except:

            print('Reload failed')
            nFail = nFail+1
        else:
            print('Checking update info')
            self.driver.implicitly_wait(10)
            self.driver.find_element_by_id('com.android.avantimarket:id/m_updateInfo').click()
            self.driver.implicitly_wait(10)
        print('Setting the name of card to Avanti')
        self.driver.find_element_by_id('com.android.avantimarket:id/m_nameOfCard').send_keys('Avanti')

        try:
            self.driver.find_element_by_id('com.android.avantimarket:id/m_doneButton').click()
            self.driver.back()
            self.driver.implicitly_wait(10)
            print('Card renamed successfully')
            nPass= nPass+1
        except:
            print('Card rename failed')
            nFail=nFail+1
        finally:
            print('Navigating to Ways to pay screen')
            self.driver.implicitly_wait(10)
        try:
            self.driver.find_element_by_id('com.android.avantimarket:id/m_cardsButton').click()
            self.driver.implicitly_wait(10)
        except:
           print('Navigating to Ways to pay screen failed')
           nFail = nFail+1
        finally:
            print('Successfully navigated to Ways to pay screen')
            nPass= nPass+1
            print('Swiping between cards')
        try:
            for x in range(0, 5):
                self.driver.swipe(start_x=950,start_y=780,end_x=150,end_y=780)
                self.driver.implicitly_wait(5)
                self.driver.swipe(start_x=150,start_y=780,end_x=950,end_y=780)
        except:
            print('Swiping cards failed')
            nFail = nFail+1
        finally:
            print('Cards swiped successfully')
            nPass= nPass+1
# Update info of ways to pay screen
        print('Updating information of card from ways to pay screen')
        try:
            self.driver.find_element_by_id('com.android.avantimarket:id/m_updateInfo').click()
            self.driver.implicitly_wait(10)
            self.driver.find_element_by_id('com.android.avantimarket:id/m_saveButton').click()
            self.driver.implicitly_wait(10)
        except:
            print('Update info failed')
            nFail = nFail+1
        finally:
            print('Update info successful')
            nPass= nPass+1
        print('Trying to cancel from update info')
        self.driver.find_element_by_id('com.android.avantimarket:id/m_updateInfo').click()
        self.driver.implicitly_wait(10)
        try:
            self.driver.find_element_by_name('CANCEL').click()
            self.driver.implicitly_wait(10)
            self.driver.back()
        except:
            print ('Cancel failed from update info')
            nFail = nFail+1
        else:
            print('Cancel successful')
            nPass= nPass+1
# Reload from main screen
        print('Attempting to reload 20$ from Main Screen')
        try:
            self.driver.find_element_by_id('com.android.avantimarket:id/m_reloadButton').click()
            self.driver.implicitly_wait(10)
        except:
            print('Reload failed')
            nFail = nFail+1
        finally:
            print('Selecting 20$ as reload amount')

        try:
            self.driver.find_element_by_id('com.android.avantimarket:id/m_twentyCheckbox').click()
            self.driver.implicitly_wait(10)
        except:
            print('Unable to select 20$')
            nFail = nFail+1
        finally:
            print('Selected 20$ as reload amount')
            nPass= nPass+1
        print('Selecting the first card from available cards')
        try:
            self.driver.find_element_by_id('com.android.avantimarket:id/m_firstCardNumber').click()
            self.driver.implicitly_wait(10)
        except:
            print('No cards present')
            nFail = nFail+1
        finally:
            print('First card selected')
            nPass= nPass+1
            self.driver.find_element_by_id('com.android.avantimarket:id/m_confirmButton').click()
            self.driver.implicitly_wait(10)
        try:
            self.driver.find_element_by_name('OK').click()
            self.driver.implicitly_wait(10)
            nPass= nPass+1
        except:
            print('Reload unsuccessful')
            nFail = nFail+1
        else:
            print('Reload from main screen for 20$ successful')

        self.driver.find_element_by_id('com.android.avantimarket:id/m_menuButton').click()
        self.driver.implicitly_wait(10)
# Support screen
        try:
            print('Navigating to support screen')
            self.driver.find_element_by_name('SUPPORT').click()
            nPass= nPass+1
        except:
            print('Failed navigating to support screen')
            nFail = nFail+1
            self.driver.implicitly_wait(5)
        finally:
            print('Navigating to helpful hints')
            self.driver.find_element_by_id('com.android.avantimarket:id/BtnHelpfulHints').click()
            self.driver.implicitly_wait(5)
        print('Navigating to Using the market screen')
        try:
            self.driver.find_element_by_id('com.android.avantimarket:id/BtnUsingTheMarket').click()
            self.driver.implicitly_wait(5)
        except:
            print('Navigating to  Using the market screen failed')
            nFail = nFail+1
        finally:
            print('Successfully navigated to Using the market screen')
            nPass= nPass+1
        print('Navigating to Setup a My MarketCard account ')
        try:
            self.driver.find_element_by_name('Setup a My MarketCard account').click()
            time.sleep(6)
        except:
            nFail = nFail+1
            print('Navigating to Setup a My MarketCard account failed')
        finally:
            print('Attempting to play video from My MarketCard account screen')
        try:
            self.driver.find_element_by_class_name('android.webkit.WebView').click()
            time.sleep(10)
        except:
                print('Video playback failed')
                nFail = nFail+1
        else:
            print('Video play back successful')
            nPass= nPass+1


        for x in range(0, 1):
            self.driver.back()
        self.driver.implicitly_wait(5)
# Sending an issue from support screen
        print('Navigating to contact us screen in support screen')
        self.driver.find_element_by_id('com.android.avantimarket:id/m_menuButton').click()
        self.driver.implicitly_wait(10)
        try:
            self.driver.find_element_by_name('SUPPORT').click()
            self.driver.implicitly_wait(5)
            self.driver.find_element_by_id('com.android.avantimarket:id/BtnContactUs').click()
            self.driver.implicitly_wait(5)
        except:
            print('Navigating to contact us screen in support screen failed')
            nFail = nFail+1
        finally:
            print('Selecting support category' )
            nPass= nPass+1
            self.driver.find_element_by_name('Select Support Category').click()
            self.driver.implicitly_wait(5)
        print('Selecting App feature Issue from drop-down')
        try:
            self.driver.find_element_by_name('App Feature Issue').click()
            self.driver.implicitly_wait(5)
        except:
            print('Failed to select App Feature issue')
            nFail = nFail+1

        finally:
            print('Selecting specific issue')
            nPass = nPass+1
            self.driver.find_element_by_name('Select Specific Issue').click()
            self.driver.implicitly_wait(5)
        try:
            print('Selecting App won’t scan an item ')
            self.driver.find_element_by_name("App won’t scan an item").click()
            self.driver.implicitly_wait(5)
        except:
            print('Selecting App won’t scan an item failed ')
            nFail = nFail+1
        finally:
            print('Selecting App won’t scan an item  successful')
            nPass= nPass+1
        print('Typing into text box')
        try:
            self.driver.find_element_by_id('com.android.avantimarket:id/et_describe').send_keys('Check successful')
            self.driver.implicitly_wait(5)
        except:
            print('Typing into text box failed')
            nFail = nFail+1
        finally:
            print('Typing into text box successful')
            nPass= nPass+1
        try:
            self.driver.hide_keyboard()

        except:
            print('Key board did not pop up as expected')

        finally:
            print('Sending request')
        try:
            self.driver.find_element_by_name('NEXT').click()
            self.driver.implicitly_wait(5)
        except:
            print('Next button not found')
        finally:
            print('Successfully tapped on next button')
            nPass=nPass+1
        try:
            print('Attempting to tap on send request')
            self.driver.find_element_by_name('SEND REQUEST').click()
            self.driver.implicitly_wait(10)
        except:
            print('Send request not found')
            nFail=nFail+1
        finally:
            print('Sending request')

            nPass= nPass+1
        try:
            self.driver.find_element_by_id('com.android.avantimarket:id/tv_thankyou_msg')

        except:
            print("Message not clear")
            nFail=nFail+1

        finally:
             print('Issue submitted successfully')
             nPass= nPass+1
        for x in range(0, 2):
            self.driver.back()
            self.driver.implicitly_wait(10)
    # Sign out

        print('Trying to Sign Out')
        self.driver.find_element_by_id('com.android.avantimarket:id/m_menuButton').click()
        try:
            self.driver.find_element_by_name('SIGN OUT').click()
            self.driver.implicitly_wait(10)
        except:
            print('No Sign out button found on menu')
            nFail = nFail+1
        finally:
            print ('Tapping on Sign out button')
        try:
            self.driver.implicitly_wait(10)
            self.driver.find_element_by_id('com.android.avantimarket:id/m_emailTextField')
            nPass = nPass + 1
        except:
            nFail = nFail+1
            print('Sign out failed')
        else:
            print('Sign out successful')
            nPass= nPass+1
# Plotting an Pie Chart for the results
        plt.rcParams.update({'font.size': 20})  # Adjust font size

        plt.pie([nPass, nFail],
                colors=["green","red"],
                labels=["Pass", "Fail"],
                autopct='%1.1f%%',
                startangle=90)

        plt.axis('equal')   # Ensure pie is round
        plt.show()
if __name__ == '__main__':
    suite = unittest.TestLoader().loadTestsFromTestCase(AvavntiAndroidTests)
    unittest.TextTestRunner(verbosity=0).run(suite)


