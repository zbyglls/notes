# Python爬虫基础
---
## 简介
    爬虫定义：网络爬虫是一种按照一定的规则，自动地抓取万维网信息的程序或者脚本。
    两大特征
        能按作者要求下载数据或者内容
        能自动在网络上流窜
    三大步骤：
        下载网页
        提取正确的信息
        根据一定规则自动跳到另外的网页上执行上两步内容
    
    Python网络包简介
        Python3.x: urllib, urllib3, httplib2, requests
        Python3：urllib，requests
## urllib
    1.包含模块
        urllib.request: 打开和读取urls
        urllib.error： 包含urllib.request产生的常见的错误，使用try捕捉
        urllib.parse:  包含解析url的方法
        urllib.robotparse: 解析robots.txt文件
```
from urllib import request

if __name__ =='__main__':
    url = 'https://www.zhaopin.com/'
    rsp = request.urlopen(url)
    #读取返回结果
    html = rsp.read()
    #解码
    html = html.decode()
    print(html)
```
    2.网页编码问题解决
        chardet：可以自动检测页面文件的编码格式，但可能有误
```
import urllib
import chardet

if __name__ == '__main__':
    url = 'https://www.51job.com/'
    rsp = urllib.request.urlopen(url)
    html = rsp.read()
    #利用chardet自动检测
    cs = chardet.detect(html)
    html = html.decode(cs.get('encoding','utf-8'))
    print(html)
```
    3.urlopen 的返回对象
        geturl：返回请求对象的url
        info：请求反馈对象的mate信息
        getcode：返回http code
```
import urllib

if __name__ == '__main__':
    url = 'https://www.51job.com/'
    rsp = urllib.request.urlopen(url)
    
    print(type(rsp))
    print(rsp)
    
    print('URL:{}'.format(rsp.geturl()))
    print('info:{}'.format(rsp.info()))
    print('code:{}'.format(rsp.getcode()))

```
    4.request.data 的使用
        访问网络的两种方法
            get: 
                利用参数给服务器传递信息
                参数为dict，然后用parse编码
```
import urllib

if __name__ == '__main__':
    url = 'http://www.baidu.com/s?'
    wd = input('input your keyword:')
    #要想使用data，需要使用字典结构
    qs = {'wd':wd}
    qs = urllib.parse.urlencode(qs)
    print(qs)
    rsp = urllib.request.urlopen(url)
    fullurl = url + qs
    print(fullurl)
    rsp = request.urlopen(fullurl)
    html = rsp.read()
    html = html.decode()
    print(html)
```
            post：
                一般向服务器传递参数使用
                post是把信息自动加密处理
                如果想使用post信息，需要用到data参数
                使用post 意味着http的请求头可能需要更改：
                    Content-Type: application/x-www.form-urlencode
                    Content-Length: 数据长度
                    简而言之，一旦更改请求方法，请注意其他请求头部信息相适应
                urllib.parse.urlencode可以将字符串自动转换成上面的
                为了更多的设置请求信息，通过urlopen函数不太好用.需要利用request.Request 类
```
from urllib import request,parse
import json

baseurl = 'https://fanyi.baidu.com/sug'
#存放用来模拟form的数据
data = {'kw': 'girl'}
data = parse.urlencode(data).encode('utf-8')
#构造请求头
headers = {'Content-Length': len(data)}
#构造一个Request的实例
req = request.Request(url=baseurl, data=data, headers=headers)
rsp = request.urlopen(req)
json_data = rsp.read().decode('utf-8')
#把json字符串转化成字典
json_data = json.loads(json_data)
for item in json_data['data']:
    print(item['k'],item['v'])
```
    5.urllib.error
        URLError产生的原因：
            没网
            服务器连接失败
            找不到指定服务器
            是OSError的子类
```
from urllib import request,error

if __name__ == '__main__':
    url = 'http://www.b2du.com'
    try:
        req = request.Request(url)
        rsp = request.urlopen(req)
        html = rsp.read().decode()
        print(html)
    except error.URLError as e:
        print('urlerror:{}'.format(e.reason))
        print('urlerror:{}'.format(e))
    except Exception as e:
        print(e)
```
        HTTPError, 是URLError的一个子类
        两者区别：
            HTTPError是对应的HTTP请求的返回码错误, 如果返回错误码是400以上的，则引发HTTPError
            URLError对应的一般是网络出现问题，包括url问题
            关系区别： OSError-URLError-HTTPError
```
from urllib import request,error

if __name__ == '__main__':
    url = 'http://www.sipo.gov.cn/www'
    try:
        req = request.Request(url)
        rsp = request.urlopen(req)
        html = rsp.read().decode()
        print(html)
    except error.HTTPError as e:
        print('HTTPerror:{}'.format(e.reason))
        print('HTTPerror:{}'.format(e))
    except error.URLError as e:
        print('URLerror:{}'.format(e.reason))
        print('URLerror:{}'.format(e))
    except Exception as e:
        print(e)
```
    6.UserAgent
        UserAgent：用户代理，简称UA，属于headers的一部分，服务器通过UA来判断访问者身份
        常见的UA值，使用的时候可以直接复制粘贴，也可以用浏览器访问的时候抓包
        
        1.Android
            Mozilla/5.0 (Linux; Android 4.1.1; Nexus 7 Build/JRO03D) AppleWebKit/535.19 (KHTML, like Gecko) Chrome/18.0.1025.166 Safari/535.19
            Mozilla/5.0 (Linux; U; Android 4.0.4; en-gb; GT-I9300 Build/IMM76D) AppleWebKit/534.30 (KHTML, like Gecko) Version/4.0 Mobile Safari/534.30
            Mozilla/5.0 (Linux; U; Android 2.2; en-gb; GT-P1000 Build/FROYO) AppleWebKit/533.1 (KHTML, like Gecko) Version/4.0 Mobile Safari/533.1
        2.Firefox
            Mozilla/5.0 (Windows NT 6.2; WOW64; rv:21.0) Gecko/20100101 Firefox/21.0
            Mozilla/5.0 (Android; Mobile; rv:14.0) Gecko/14.0 Firefox/14.0
        3.Google Chrome
            Mozilla/5.0 (Windows NT 6.2; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/27.0.1453.94 Safari/537.36
            Mozilla/5.0 (Linux; Android 4.0.4; Galaxy Nexus Build/IMM76B) AppleWebKit/535.19 (KHTML, like Gecko) Chrome/18.0.1025.133 Mobile Safari/535.19
        4.iOS
            Mozilla/5.0 (iPad; CPU OS 5_0 like Mac OS X) AppleWebKit/534.46 (KHTML, like Gecko) Version/5.1 Mobile/9A334 Safari/7534.48.3
            Mozilla/5.0 (iPod; U; CPU like Mac OS X; en) AppleWebKit/420.1 (KHTML, like Gecko) Version/3.0 Mobile/3A101a Safari/419.3
        设置UA可以通过两种方式：
            headers
            add_header
```
from urllib import request, parse, error

if __name__ == '__main__':
    url = 'http://httpbin.org/post'
    try:
        data = {'name':'linsan'}
        data = parse.urlencode(data).encode('utf-8')

        #通过headers构造
        #headers = {'User-Agent':'Mozilla/5.0 (Linux; Android 4.1.1; Nexus 7 Build/JRO03D) AppleWebKit/535.19 (KHTML, like Gecko) Chrome/18.0.1025.166 Safari/535.19'}
        #req = request.Request(url, data=data, headers=headers)

        #通过add_header构造
        req =request.Request(url, data=data)
        req.add_header('User-Agent','Mozilla/5.0 (Linux; Android 4.1.1; Nexus 7 Build/JRO03D) AppleWebKit/535.19 (KHTML, like Gecko) Chrome/18.0.1025.166 Safari/535.19')
        
        rsp = request.urlopen(req)
        html = rsp.read().decode('utf-8')
        print(html)
    except error.HTTPError as e:
        print(e)
    except error.URLError as e:
        print(e)
    except Exception as e:
        print(e)
```
    7.ProxyHandler处理（代理服务器）
        使用代理IP
        获取代理服务器的地址：
            www.xicidaili.com
            www.goubanjia.com
        代理用来隐藏真实访问中，代理也不允许频繁访问某一个固定网站，所以，代理一定要很多
        基本使用步骤：
        1. 设置代理地址
        2. 创建ProxyHandler
        3. 创建Opener
        4. 安装Opener
```
from urllib import request, error

if __name__ == '__main__':
    url = 'http://www.badu.com'
    #设置代理地址
    proxy = {'http':'113.88.26.148:8118'}
    #创建ProxyHandler
    proxy_handler = request.ProxyHandler(proxy)
    #创建Opener
    opener = request.build_opener(proxy_handler)
    #安装Opener
    request.install_opener(opener)
    
    try:
        rsp = request.urlopen(url)
        html = rsp.read().decode()
        print(html)
    except error.URLError as e:
        print(e)
    except Exception as e:
        print(e)
```
    8.cookie & session
        由于http协议的无记忆性，为了弥补这个缺憾，所采用的一个补充协议
        cookie是发放给用户（即http浏览器）的一段信息，session是保存在服务器上的对应的另一半信息，用来记录用户信息
        
        cookie和session的区别
            存放位置不同
            cookie不安全
            session会保存在服务器上一定时间，会过期
            单个cookie保存数据不超过4k， 很多浏览器限制一个站点最多保存20个
        session的存放位置
            存在服务器端
            一般情况，session是放在内存中或者数据库中
            没使用cookie则反馈网页为未登录状态
    使用cookie登录
        直接把cookie复制下来，然后手动放入请求头
```
from urllib import request

if __name__ == '__main__':
    url = 'https://study.163.com/'

    headers = {
        'Cookie':'cookie'
    }
    req = request.Request(url, headers=headers)
    rsp = request.urlopen(req)
    html = rsp.read().decode()
    print(html)
    with open('rsp.html','w', encoding='utf-8') as target:
        target.write(html)
```
    9.http模块包含一些关于cookie的模块，通过他们我们可以自动使用cookie
        CookieJar
            管理存储cookie，向传出的http请求添加cookie，
            cookie存储在内存中，CookieJar实例回收后cookie将消失
        FileCookieJar(filename, delayload=None, policy=None):
            使用文件管理cookie
            filename是保存cookie的文件
        MozillaCookieJar(filename, delayload=None, policy=None):
            创建与mozilla浏览器cookie.txt兼容的FileCookieJar实例
        LwpCookieJar(filename, delayload=None, policy=None):
            创建与libwww-perl标准兼容的Set-Cookie3格式的FileCookieJar实例
        他们的关系是: CookieJar-->FileCookieJar-->MozillaCookieJar & LwpCookieJar
```
#利用cookiejar访问人人网案例
from urllib import request, parse
from http import cookiejar

'''
自动使用cookie登录，大致流程是
打开登录页面后自动通过用户名密码登录
自动提取反馈回来的cookie
利用提取的cookie登录隐私页面
'''
#创建cookiejar的实例
cookie = cookiejar.CookieJar()
#生成cookie的管理器
cookie_handler = request.HTTPCookieProcessor(cookie)
#创建http请求管理器
http_handler = request.HTTPHandler()
#生成https管理器
https_handler = request.HTTPSHandler()
#创建请求管理器
opener = request.build_opener(http_handler, https_handler, cookie_handler)
    
def login():
    url = 'http://www.renren.com/PLogin.do'
    data = {
        'email':'',
        'password':''
    }
    #把数据进行编码
    data = parse.urlencode(data)
    #创建一个请求对象
    req = request.Request(url, data=data.encode())
    #使用opener发起请求
    rsp = opener.open(req)

def getHomePage():
    url = 'http://www.renren.com/965187997/profile'
    rsp = opener.open(url)
    html = rsp.read().decode()
    with open('rsp.html', 'w',encoding='utf-8') as f:
        f.write(html)

if __name__ == "__main__":
    login()
    getHomePage()

```
    10.handler是Handler的实例
        用来处理复杂请求
            #生成 cookie的管理器
            cookie_handler = request.HTTPCookieProcessor(cookie)
            #创建http请求管理器
            http_handler = request.HTTPHandler()
            #生成https管理器
            https_handler = request.HTTPSHandler()
        创建handler后，使用opener打开，打开后相应的业务由相应的hanlder处理
        
        cookie的属性
            name: 名称
            value：值
            domain：可以访问此cookie的域名
            path：可以访问此cookie的页面路径
            expires：过期时间
            size：大小
            Http字段
        cookie的保存，读取-FileCookieJar
```
#保存
from urllib import request, parse
from http import cookiejar

#创建filecookiejar的实例
filename = 'cookie.txt'
cookie = cookiejar.MozillaCookieJar(filename)
#生成cookie的管理器
cookie_handler = request.HTTPCookieProcessor(cookie)
#创建http请求管理器
http_handler = request.HTTPHandler()
#生成https管理器
https_handler = request.HTTPSHandler()
#创建请求管理器
opener = request.build_opener(http_handler, https_handler, cookie_handler)
    
def login():
    url = 'http://www.renren.com/PLogin.do'

    data = {
        'email':'13119144223',
        'password':'123456'
    }
    #把数据进行编码
    data = parse.urlencode(data)
    #创建一个请求对象
    req = request.Request(url, data=data.encode())
    #使用opener发起请求
    rsp = opener.open(req)

    #保存cookie
    #ignore_discard表示即使cookie将要被丢弃也保存下来
    #ignore_expires表示即使cookie过期也保存
    cookie.save(ignore_discard=True, ignore_expires=True)

if __name__ == "__main__":
    login()
```
```
#读取
from urllib import request, parse
from http import cookiejar
#创建cookiejar的实例
cookie = cookiejar.MozillaCookieJar()
cookie.load('cookie.txt', ignore_discard=True, ignore_expires=True)
#生成cookie的管理器
cookie_handler = request.HTTPCookieProcessor(cookie)
#创建http请求管理器
http_handler = request.HTTPHandler()
#生成https管理器
https_handler = request.HTTPSHandler()
#创建请求管理器
opener = request.build_opener(http_handler, https_handler, cookie_handler)
def getHomePage():
    url = 'http://www.renren.com/965187997/profile'
    rsp = opener.open(url)

    html = rsp.read().decode()
    with open('rsp.html', 'w',encoding='utf-8') as f:
        f.write(html)

if __name__ == "__main__":
    getHomePage()
```
    11.SSL
        SSL证书就是指遵守SSL安全套阶层协议的服务器数字证书（SercureSocketLayer)
        CA（CertifacateAuthority)是数字证书认证中心，是发放，管理，废除数字证书的收信人的第三方机构
        遇到不信任的SSL证书，需要单独处理
```
from urllib import request
import ssl

ssl._create_default_https_context = ssl._create_unverified_context
url = 'https://www.12306.cn/mormhweb/'
rsp = request.urlopen(url)

html = rsp.read().decode()
print(html)
```
    12.js加密
        有的反爬虫策略采用js对需要传输的数据进行加密处理（通常是取md5值)
        经过加密，传输的就是密文，但是加密函数或者过程一定是在浏览器完成，也就是一定会把代码（js代码）暴露给使用者
        通过阅读加密算法，就可以模拟出加密过程，从而达到破解
```
from urllib import request, parse
#处理js代码
'''
查找js代码中操作代码
1.计算salt的公式 i = "" + (new Date).getTime() + parseInt(10 * Math.random(), 10)
2.sign：n.md5("fanyideskweb" + e + i + "Nw(nmmbP%A-r6U3EUn]Aj")
MD5一共需要四个参数，第一个和第四个是固定的字符串，第三个是是salt，第二个是输入要查找的单词
'''
def getSalt():
    '''
    salt的公式 ："" + (new Date).getTime() + parseInt(10 * Math.random(), 10)
    翻译成python代码
    '''
    import time, random

    salt = int(time.time()*1000) + random.randint(0,10)
    return salt
def getMD5(v):
    import hashlib
    md5 = hashlib.md5()
    #update需要一个bytes格式的参数
    md5.update(v.encode('utf-8'))
    sign = md5.hexdigest()

    return sign
def getSign(key, salt):
    sign = 'fanyideskweb' + key + str(salt) + 'Nw(nmmbP%A-r6U3EUn]Aj'
    sign = getMD5(sign)
    return sign

def youdao(key):
    url = 'http://fanyi.youdao.com/translate_o?smartresult=dict&smartresult=rule'

    salt = getSalt()
    data = {
        'i': key,
        'from': 'AUTO',
        'to': 'AUTO',
        'smartresult': 'dict',
        'client': 'fanyideskweb',
        'salt': str(salt),
        'sign': getSign(key, salt),
        'ts': '1583326788271',
        'bv': '0ed2e07b89acaa1301d499442c9fdf79',
        'doctype': 'json',
        'version': '2.1',
        'keyfrom': 'fanyi.web',
        'action': 'FY_BY_REALTlME'
    }
    data =parse.urlencode(data).encode()
    headers = {
        'Accept': 'application/json, text/javascript, */*; q=0.01',
        #'Accept-Encoding': 'gzip, deflate',
        'Accept-Language': 'zh-CN,zh;q=0.9',
        'Connection': 'keep-alive',
        'Content-Length': len(data),
        'Content-Type': 'application/x-www-form-urlencoded; charset=UTF-8',
        'Cookie': 'OUTFOX_SEARCH_USER_ID=716417750@10.169.0.84; OUTFOX_SEARCH_USER_ID_NCOO=1639474591.1288674; JSESSIONID=aaaK1n1kkytQV_IiGNLcx; ___rl__test__cookies=1583326788266',
        'Host': 'fanyi.youdao.com',
        'Origin': 'http://fanyi.youdao.com',
        'Referer': 'http://fanyi.youdao.com/',
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.122 Safari/537.36',
        'X-Requested-With': 'XMLHttpRequest'
    }
    req = request.Request(url=url, data=data, headers=headers)
    rsp = request.urlopen(req)
    html = rsp.read().decode()
    print(html)

if __name__ == "__main__":
    youdao('girl')

```
    13.ajax
        异步请求
        一定会有url，请求方法，可能有数据
        一般使用json格式
```
'''
爬取豆瓣
了解ajax的基本爬取方式
'''
from urllib import request
import json

url = 'https://movie.douban.com/j/chart/top_list?type=24&interval_id=100%3A90&action=&start=20&limit=20'

headers = {
    'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.122 Safari/537.36'
}
req = request.Request(url, headers=headers)
rsp = request.urlopen(req)
data = rsp.read().decode()
data = json.loads(data)
print(data)
```
## Requests
    继承了urllib的所有特征；底层使用的是urllib3
    开源地址： https://github.com/requests/requests
    中文文档： http://docs.python-requests.org/zh_CN/latest/index.html
    1.get请求
        requests。get()
        requests.request("get", url)
        可以带有headers和parmas参数
```
import requests

url = 'http://www.51job.com'

#使用get请求
rsp = requests.get(url)
print(rsp.text)

#使用request请求
rsp = requests.request('get',url)
print(rsp.content)
```
    2.get返回内容
```
'''
使用参数headers和params研究返回结果
'''
import requests

url = 'http://www.baidu.com/s?'

kw = {
    'wd': '51'
}
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.122 Safari/537.36'
}
rsp = requests.get(url, params=kw, headers=headers)

print(rsp.text.)
print(rsp.content)
print(rsp.url)
print(rsp.encoding)
print(rsp.status_code)#返回码
```
    3.post
        rsp = requests.post(url, data=data)
        date, headers要求dict类型
```
import requests

url = 'https://fanyi.baidu.com/sug'

data = {
    'kw': 'girl'
}
headers = {
    'Content-Length':str(len(data))
}
rsp = requests.post(url, data=data, headers=headers)

print(rsp.text)
print(rsp.json())
```
    4. proxy
            proxies = {
            "http":"address of proxy",
            "https": "address of proxy"
            }
            rsp = requests.request("get", url, proxies=proxies)
        代理有可能报错，如果使用人数多，考虑安全问题，可能会被强行关闭
    5.用户验证
        代理验证
            #可能需要使用HTTP basic Auth
            #格式为  用户名:密码@代理地址：端口地址
            proxy = { "http": "china:123456@192.168.1.123：4444"}
            rsp = requests.get(url, proxies=proxy)
        web客户端验证
            如果遇到web客户端验证，需要添加auth=（用户名，密码）
                autu=("test1", "123456")#授权信息
                rsp = requests.get(url, auth=auth)
    6.cookie
        requests可以自动处理cookie信息
            rsp = requests.get("http://xxxxxxxxxxx")
            #如果对方服务器给传送过来cookie信息，则可以通过反馈的cookie属性得到
            #返回一个cookiejar实例
            cookiejar = rsp.cookies   
            #可以将cookiejar转换成字典
            cookiedict = requests.utils.dict_from_cookiejar(cookiejar)
    7.session
        跟服务器端session不是一个东西
        模拟一次会话，从客户端浏览器链接服务器开始，到客户端浏览器断开
        能让我们跨请求时保持某些参数，比如在同一个session实例发出的 所有请求之间保持cookie
            #创建session对象，可以保持cookie值
            ss = requests.session()
            headers = {"User-Agetn":"xxxxxxxxxxxxxxxxxx"}
            data = {"name":"xxxxxxxxxxx"}
            #此时，由创建的session管理请求，负责发出请求，
            ss.post(url, data=data, headers=headers)
            rsp = ss.get(url)
    8.https请求验证ssl证书
        参数verify负责表示是否需要验证ssL证书，默认是True
        如果不需要验证ssl证书，则设置成False表示关闭
            rsp = requests.get(url, verify=False)
            #如果用verify=True访问12306，会报错，因为他证书有问题 
## 页面解析和数据提取
    结构数据： 先有的结构，在谈数据
        JSON文件
            JSON Path
            转换成Python类型进行操作（json类）
        XML文件
            转换成python类型（xmltodict）
            XPath
            CSS选择器
            正则
    非结构化数据：先有数据，再谈结构
        文本, 电话号码, 邮箱地址
            通常处理此类数据，使用正则表达式
        Html文件
            正则
            XPath
            CSS选择器
## 正则表达式
    一套规则，可以在字符串文本中进行搜查替换等
    https://www.w3school.com.cn/python/python_regex.asp
    1.re的基本使用流程
```
'''
re使用大致步骤：
1. compile函数将正则表达式的字符串编译为一个Pattern对象
2. 通过Pattern对象的一些列方法对文本进行匹配，匹配结果是一个Match对象
3. 用Match对象的方法，对结果进行操纵
'''
import re

#\d表示数字
#后面+号表示这个数字可以出现一次或者多次
s = r"\d+" # r表示后面是原生字符串，后面不需要转义

#返回Pattern对象
pattern = re.compile(s)

#返回一个Match对象
#默认找到一个匹配就返回
m = pattern.match("one12two2three3")

print(type(m))
#默认匹配从头部开始，所以此次结果为None
print(m)

#返回一个Match对象
#后面为位置参数含义是从哪个位置开始查找，找到哪个位置结束
m = pattern.match("one12two2three3", 3, 10)

print(type(m))
#默认匹配从头部开始，所以此次结果为None
print(m)

print(m.group())

print(m.start(0))
print(m.end(0))
print(m.span(0))
```
    2.match的基本使用
```
import re

s = r'([a-z]+) ([a-z]+)'
pattern = re.compile(s, re.I)#re.I表示忽略大小写

m = pattern.match('hello workd wide web')

#group(0)表示返回匹配成功的整个子串
s= m.group(0)
print(s)

#返回匹配 成功的整个字串的跨度
a = m.span(0)
print(a)

#group(1)表示返回的第一个分组匹配成功的子串
s = m.group(1)
print(s)

#返回匹配成功的第一个字串的跨度
a = m.span(1)
print(a)

s = m.groups()#等价于m.group(1),m.group(2)......
print(s)
```
    3.正则常用方法：
        match: 从开始位置开始查找，一次匹配
        search：从任何位置查找，一次匹配
        findall： 全部匹配，返回列表
        finditer： 全部匹配，返回迭代器
        split： 分割字符串，返回列表
        sub：替换
```
#search
import re

s = r"\d+" 
pattern = re.compile(s)
m = pattern.search("one12two2three56")
print(m.group())
#参数表示搜查的起始范围
m = pattern.search("one12two2three56", 10, 40)
print(m.group())

#findall
pattern = re.compile(r'\d+')
s = pattern.findall('i am 18 years old and 170 high')
print(s)

#finditer
s = pattern.finditer('i am 18 years old and 170 high')
print(type(s))
for i in s:
    print(i.group())
```
    4.匹配中文
        中文unicode范围主要在[u4e00-u9fa5]
```
import re

hello = u'你好，世界'
pattern = re.compile(r'[\u4e00-\u9fa5]+')
m = pattern.findall(hello)
print(m)
```
    5.贪婪与非贪婪模式
        贪婪模式： 在整个表达式匹配成功的前提下，尽可能多的匹配
        非贪婪模式： xxxxxxxxxxxxxxxxxxxxxx, 尽可能少的匹配
        python里面数量词默认是贪婪模式
        例如：
            查找文本abbbbbbccc
            re是 ab*
            贪婪模式： 结果是abbbbbb
            非贪婪： 结果是a
## XML(EXtensibleMarkupLanguage)   
    http://www.w3school.com.cn/xml/index.asp
    概念：父节点，子节点，先辈节点，兄弟节点，后代节点
```
<?xml version="1.0" encoding="utf-8"?>
<bookstore>
    <boook category="cooking">
        <title lang="en">everyday italian</title>
        <author>Gidada</author>
        <year>2018</year>
        <price>23</price>
    </boook>

    <boook category="education">
        <title lang="en">python is python</title>
        <author>food war</author>
        <year>2008</year>
        <price>83</price>
    </boook>

    <boook category="sport">
        <title lang="en">running</title>
        <author>klaus kuka</author>
        <year>2010</year>
        <price>43</price>
    </boook>
</bookstore>
```
## XPath(XML Path Language) 
    是一门在XML文档中查找信息的语言
    官方文档： http://www.w3school.com.cn/xpath/index.asp
    1>XPath开发工具
        开元的XPath表达式工具： XMLQuire
        chrome插件： Xpath Helper
        Firefox插件： XPath CHecker
        
    2>常用路径表达式：
        nodename: 选取此节点的所有子节点
        /: 从根节点开始选
        //: 选取元素，而不考虑元素的具体为止
        .:  当前节点
        ..:父节点
        @： 选取属性
        案例：
            booksotre: 选取bookstore下的所有子节点
            /booksotre: 选取根元素
            booksotre/book: 选取bookstore的所有为book的子元素
            //book: 选取book子元素
            //@lang:选取名称为lang的所有属性
    3>谓语(Predicates)
        谓语用来查找某个特定的节点，被向前在方括号中
        /bookstore/book[1]: 选取第一个属于bookstore下叫book的元素
        /bookstore/book[last()]: 选取最后一个属于bookstore下叫book的元素
        /bookstore/book[last()-1]: 选取倒数第二个属于bookstore下叫book的元素
        /bookstore/book[position()<3]: 选取属于bookstore下叫book的前两个元素
        /bookstore/book[@lang]: 选取属于bookstore下叫book的,含有属性lang元素
        /bookstore/book[@lang="cn"]: 选取属于bookstore下叫book的,含有属性lang的值是cn的元素
        /bookstore/book[@price < 90]: 选取属于bookstore下叫book的,含有属性price的，且值小于90的元素
        /bookstore/book[@price < 90]/title: 选取属于bookstore下叫book的,含有属性price的，且值小于90的元素的子元素title
        
    4>通配符
        `*` : 任何元素节点
        @*： 匹配任何属性节点
        node(): 陪陪任何类型的节点
    5>选取多个路径
        //book/tile  | //book/author : 选取book元素中的title和author元素
        //tile | //price: 选取文档中所有的title和price元素
## lxml库
    python的HTML/XML的解析器
    官方文档：http://lxml.de/index.html
```
from lxml import etree

'''
用lxml解析HTML代码
'''
text = '''
<div>
    <ul>
        <li class="item-0"> <a href="0.html"> first item </a></li>
        <li class="item-1"> <a href="1.html"> first item </a></li>
        <li class="item-2"> <a href="2.html"> first item </a></li>
        <li class="item-3"> <a href="3.html"> first item </a></li>
        <li class="item-4"> <a href="4.html"> first item </a></li>
        <li class="item-5"> <a href="5.html"> first item </a>
    </ul>
</div>
'''
#利用etree.HTML把字符解析成HTML文档
html = etree.HTML(text)
s = etree.tostring(html)
print(s)

#文件读取
from lxml import etree

#只能读取xml格式内容
html = etree.parse('./30.html')
rst = etree.tostring(html, pretty_print=True)
print(rst)

#etree和XPath的配合使用
from lxml import etree

#只能读取xml格式内容
html = etree.parse('./30.html')

rst = html.xpath('//book')
print(type(rst))
print(rst)

rst = html.xpath('//book[@category="sport"]')
print(rst)

rst = html.xpath('//book[@category="sport"]/year')
rst = rst[0]
print(rst.tag)
print(rst.text)
```
## CSS选择器  BeautifulSoup4
    http://beautifulsoup.readthedocs.io/zh_CN/v4.4.0/
    1.几个常用提取信息工具的比较：
        正则： 很快，不好用，不许安装
        beautifulsoup：慢，使用简单，安装简单
        lxml： 比较快，使用简单，安装一般
```
from urllib import request
from bs4 import BeautifulSoup

url = 'https://wwww.baidu.com'

rsp = request.urlopen(url)
content = rsp.read()
soup = BeautifulSoup(content,'lxml')

#bs自动转码
content = soup.prettify()
print(content)
```
    2.四大对象
        Tag
        NavigableString
        BeautifulSoup
        Comment
    3.Tag
        对应Html中的标签
        可以通过soup.tag_name
        tag两个重要属性
            name
            attrs
```
from urllib import request
from bs4 import BeautifulSoup

url = 'http://www.baidu.com'

rsp = request.urlopen(url)
content = rsp.read()
soup = BeautifulSoup(content,'lxml')

#bs自动转码
content = soup.prettify()
#print(soup.head)
#print(soup.meta)
print(soup.link)
print(soup.link.name)
print(soup.link.attrs)
print(soup.link.attrs['type'])
```
    4.NavigableString
        对应内容值
```
from urllib import request
from bs4 import BeautifulSoup

url = 'http://www.baidu.com'

rsp = request.urlopen(url)
content = rsp.read()
soup = BeautifulSoup(content,'lxml')
content = soup.prettify()
print(soup.title)
print(soup.title.name)
print(soup.title.attrs)
print(soup.title.string)
```
    5.BeautifulSoup
        表示的是一个文档的内容，大部分可以把他当做tag对象
        一般可以用soup来表示
    6.Comment
        特殊类型的NavagableString对象， 
         对其输出，则内容不包括注释符号
    7.遍历文档对象
        contents: tag的子节点以列表的方式给出 
        children：子节点以迭代器形式返回 
        descendants：所子孙节点
        string
```
from urllib import request
from bs4 import BeautifulSoup

url = 'http://www.baidu.com'

rsp = request.urlopen(url)
content = rsp.read()
soup = BeautifulSoup(content,'lxml')

for node in soup.head.contents:
    if node.name == 'meta':
        print(node)
    if node.name == 'title':
        print(node.string)
```
    8.搜索文档对象
        find_all(name, attrs, recursive, text, ** kwargs)  
            name:按照那个字符串搜索，可以传入的内容为：字符串,正则表达式,列表
            keyworld参数，可以用来表示属性
            text： 对应tag的文本值
```
from urllib import request
from bs4 import BeautifulSoup
import re

url = 'http://www.baidu.com'

rsp = request.urlopen(url)
content = rsp.read()
soup = BeautifulSoup(content,'lxml')

tags = soup.find_all(name='meta')
print(tags)

tags = soup.find_all(re.compile('^me'))
for tag in tags:
    print(tag)
```
    9.css选择器
        使用soup.select, 返回一个列表
        通过标签名称: soup.select("title")            
        通过类名： soup.select(".content")
        id查找: soup.select("#name_id")
        组合查找: soup.select("div #input_content")
        属性查找: soup.select("img[class='photo'])
        获取tag内容： tag.get_text
```
from urllib import request
from bs4 import BeautifulSoup

url = 'http://www.baidu.com'

rsp = request.urlopen(url)
content = rsp.read()
soup = BeautifulSoup(content,'lxml')

titles = soup.select('title')
print(titles[0])

metas = soup.select('meta[content="always"]')
print(metas[0])
```
## Selenium + PhantomJS
    1.Selenium: web自动化测试工具
        自动加载页面，获取数据，截屏
        官网：http://selenium-python.readthedocs.io/index.html
    2.PhantomJS(幽灵)
        基于Webkit 的无界面的浏览器 
        官网：http://phantomjs.org/download.html
    Selenium 库有有一个WebDriver的API
    WebDriver可以跟页面上的元素进行各种交互，用它可以来进行爬取
```
from selenium import webdriver
import time
#通过Keys模拟键盘
from selenium.webdriver.common.keys import Keys

driver = webdriver.PhantomJS()

driver.get('http://www.baidu.com')

print('Title:{}'.format(driver.title))
```
    3.Selenium操作主要分两大类：
        得到UI元素
            find_element_by_id
            find_elements_by_name
            find_elements_by_xpath
            find_elements_by_link_text
            find_elements_by_partial_link_text
            find_elements_by_tag_name
            find_elements_by_class_name
            find_elements_by_css_selector
        基于UI元素操作的模拟
            单击, 右键, 拖拽, 输入
            可以通过导入ActionsChains类来做到
```
from selenium import webdriver
import time
#通过Keys模拟键盘
from selenium.webdriver.common.keys import Keys

url = 'http://www.baidu.com'
driver = webdriver.Chrome()
driver.get(url)

text = driver.find_element_by_id('wrapper').text
print(text)
print(driver.title)
#得到页面的快照
driver.save_screenshot('index.png')
#id="kw" 的是百度的输入框，我们得到输入框的ui元素后直接输入“大熊猫"
driver.find_element_by_id('kw').send_keys('大熊猫')

#id="su"是百度搜索的按钮，click模拟点击
driver.find_element_by_id('su').click()
time.sleep(5)
driver.save_screenshot("daxiongmao.png")

#获取当前页面的cookie
print(driver.get_cookies())
#模拟输入两个按键 ctrl+ a
driver.find_element_by_id('kw').send_keys(Keys.CONTROL, 'a')
#ctr+x 是剪切快捷键
driver.find_element_by_id('kw').send_keys(u'航空母舰')

driver.find_element_by_id('su').send_keys(Keys.RETURN)
time.sleep(5)
driver.save_screenshot('hangmu.png')

driver.find_element_by_id('kw').clear()
driver.save_screenshot('clear.png')
#关闭浏览器
driver.quit()

```

