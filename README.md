# python_auto_post_bot

###0527 test

from selenium import webdriver
import time
                   
###登入帳號
browser = webdriver.Chrome()
url = 'https://www.dcard.tw/signup'
browser.get(url)                    # 網頁下載至瀏覽器

txtBox = browser.find_element_by_id('email')
txtBox1 = browser.find_element_by_id('password')
txtBox.send_keys('你的帳號')          # 輸入表單資料
txtBox1.send_keys('你的密碼')          # 輸入表單資料

time.sleep(2)                       # 暫停2秒
txtBox.submit()                     # 送出表單


###why so serious://*[@id="__next"]/div[2]/div[1]/div/div/div[1]/div[2]/div/div/div/span[2]/a[3]/div/div/div[1]
###post://*[@id="__next"]/div[1]/div/div[2]/a[1]/span/svg

###跳轉到廢版
drive = webdriver.Chrome()
new_url = 'https://www.dcard.tw/f'
drive.get(new_url)                    # 網頁下載至瀏覽器
time.sleep(2)                       # 暫停2秒
btnBox = browser.find_element_by_xpath('//*[@id="__next"]/div[2]/div[1]/div/div/div[1]/div[2]/div/div/div/span[2]/a[3]/div/div/div[1]')
btnBox.click()

time.sleep(1)                       # 暫停1秒
drive.close()

###跳轉到發文介面
new_drive = webdriver.Chrome()
new_url = 'https://www.dcard.tw/f/whysoserious'
new_drive.get(new_url)                    # 網頁下載至瀏覽器

postBox = browser.find_element_by_xpath('//*[@id="__next"]/div[1]/div/div[2]/a[1]')
postBox.click()

time.sleep(1)                       # 暫停1秒

new_drive.close()

###點擊發文介面內的哪個版和填寫內文
###why so serious btn:/html/body/div[2]/div/div[2]/div/div/div[2]/div/div/div[1]/div[2]/div/div/div/div/div[5]/div/div
###/html/body/div[2]/div/div[2]/div/div/div[2]/div/div/div[1]/div[2]/div/div/div/div/div[5]/div/div
###full xpath /html/body/div[2]/div/div[2]/div/div/div[2]/div/div/div[1]/div[2]/div/div/div/div/div[5]/div/div
sec_drive = webdriver.Chrome()
new_url = 'https://www.dcard.tw/new-post'
sec_drive.get(new_url)                    # 網頁下載至瀏覽器

###點擊發文格事前可能會擋(取消驗證)
clk_cheakpersonalmess_Box = browser.find_element_by_xpath('/html/body/div[2]/div/div[2]/div/footer/div[1]/button/div')
clk_cheakpersonalmess_Box.click()
###點選最外圍看板按鈕
clk_board_Box_first = browser.find_element_by_xpath('//*[@id="__next"]/main/form/div[2]/div[1]/div/div/div')
clk_board_Box_first.click()
###點選廢文按鈕
clk_board_Box_second = browser.find_element_by_xpath('/html/body/div[2]/div/div[2]/div/div/div[2]/div/div/div[1]/div[2]/div/div/div/div/div[5]/div/div')
clk_board_Box_second.click()
###點選最外圍學校按鈕
clk_school_Box_first = browser.find_element_by_xpath('//*[@id="__next"]/main/form/div[3]/div/div/div/div[2]/div/div/div')
clk_school_Box_first.click()
time.sleep(0.5)
###點選學校按鈕
clk_school_Box_second = browser.find_element_by_xpath('/html/body/div[2]/div/div/div/div/div/div[1]/div/button[2]/span/div/div/div/div/div')
clk_school_Box_second.click()
###點選卡稱按鈕
#clk_nickname_Box_second = browser.find_element_by_xpath('/html/body/div[2]/div/div/div/div/div/div[1]/div/button[3]/span/div/div/div/div/div')
#clk_nickname_Box_second.click()
###自動填入標題
try:
    clk_title_Box = browser.find_element_by_xpath('//*[@id="__next"]/main/form/div[3]/textarea')
    clk_title_Box.send_keys('填入你的標題')
except:
    clk_title_Box = browser.find_element_by_xpath('//*[@id="__next"]/main/form/div[3]/textarea')
    clk_title_Box.send_keys('')
    
###自動填入內文
clk_content_Box = browser.find_element_by_xpath('//*[@id="__next"]/main/form/div[4]/div/div[1]/div[2]')
#clk_content_Box.send_keys('%d %d %d %d %d %d\n'%(arr[0],arr[1],arr[2],arr[3],arr[4],arr[5]))
clk_content_Box.send_keys('填入你的內文')
###按下一步鈕
clk_next_Box = browser.find_element_by_xpath('//*[@id="__next"]/main/form/div[4]/div/div[2]/div/div[2]/button')
clk_next_Box.click()
###新增話題
add_tag_Box = browser.find_element_by_xpath('/html/body/div[2]/div/div[2]/div/div/label/div/div[1]/div/input')
add_tag_Box.send_keys('填入你的話題')
time.sleep(5)                       # 暫停2秒
###按下相對應話題
clk_tag_Box = browser.find_element_by_xpath('/html/body/div[2]/div/div[2]/div/div/label/div/div[2]/div[1]')
clk_tag_Box.click()
###按下發送鈕
clk_sent_Box = browser.find_element_by_xpath('/html/body/div[2]/div/div[2]/div/footer/div[2]/button')
clk_sent_Box.click()
time.sleep(2)                       # 暫停2秒
sec_drive.close()

###印出現在文章的連結
current_url = browser.current_url
print(current_url)
