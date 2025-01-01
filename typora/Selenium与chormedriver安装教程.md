# Selenium与chormedriver安装教程（Author: Wuiris）

## <font color='red'>本次教程环境：python 3.12.4; chrome131.0.6778.205；pycharm：2024.1.6</font>

Selenium是外部库，故需要使用pip命令安装。由于比较大，建议使用国内镜像源进行安装

```shell
pip install selenium
```

当然，只有selenium没什么用，我们需要安装对应的webdriver，这里演示chromedriver的安装

首先打开chrome，在网址栏输入`chrome://version/`, 记住你的版本号

![image-20241231222723627](https://raw.githubusercontent.com/wutongbenshu/Tu-chuang/main/typora/image-20241231222723627.png)

然后打开`https://googlechromelabs.github.io/chrome-for-testing/`，找到自己的对应版本（若是版本太老（114之前）请移步`https://chromedriver.storage.googleapis.com/index.html`），注意选对平台

![image-20241231223314610](https://raw.githubusercontent.com/wutongbenshu/Tu-chuang/main/typora/image-20241231223314610.png)

下载完成后对其进行解压（注意下载chromedriver，而不是其它的），解压到python文件夹（或conda）下，确保chromedriver.exe在这一级目录。

![image-20241231225153257](https://raw.githubusercontent.com/wutongbenshu/Tu-chuang/main/typora/image-20241231225153257.png)

然后打开你心爱的pycharm，输入如下代码, 进行测试。出现如下界面则说明一切正常

```python
from selenium import webdriver

chrome = webdriver.Chrome()
chrome.get('https://www.baidu.com/')

input()

```

![image-20241231225335583](https://raw.githubusercontent.com/wutongbenshu/Tu-chuang/main/typora/image-20241231225335583.png)

## 一些报错

### 1.selenium.common.exceptions.NoSuchDriverException

![image-20241231225521380](https://raw.githubusercontent.com/wutongbenshu/Tu-chuang/main/typora/image-20241231225521380.png)

出现这种错误的，说明你的chromedriver.exe没有配置对，或者环境变量不对。可以通过如下代码解决。

```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service


chrome = webdriver.Chrome(service=Service(r'你的chromedriver.exe的具体路径'))
chrome.get('https://www.baidu.com/')

input()

```

这适用于selenium4以上版本，如果为旧版本，请使用如下代码

```python
from selenium import webdriver

chrome = webdriver.Chrome(executable_path=r'你的chromedriver.exe的具体路径')
chrome.get('https://www.baidu.com/')

input()

```

### 2.Exception managing chrome: error sending request for url (https://googlechromelabs.github.io/chrome-for-testing/known-good-versions-with-downloads.json)

这是因为github.io国内链接不稳定，不影响使用

### 3.欢迎补充
