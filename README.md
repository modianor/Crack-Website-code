# WEIBO-OCR
新浪微博的验证码识别（样本1万）
识别微博验证码
![](https://github.com/LoseNine/WEIBO-OCR/blob/master/2bc2w.png)

## 开放OCR.dll方法
```
  getOCR(mcg,img)
```

## 实例
```python

import ctypes
class OCR:
    def __init__(self):
        self.dll=None
        self.setDll()
    def setDll(self):
        #加载DLL
        self.dll=ctypes.CDLL("./OCR.dll")
    def getOCR(self,mcg,img):
        #输入dat地址和图片地址
        imgPath = img.encode('utf8')
        img = ctypes.create_string_buffer(imgPath)

        mcgPath = mcg.encode('utf8')
        mcg = ctypes.create_string_buffer(mcgPath)
        result=ctypes.string_at(self.dll.getOCR(mcg, img))
        return result.decode('gb2312')

if __name__ == '__main__':
    c=OCR()
    print(c.getOCR("D:/codes/DLL/mcg.dat","D:/codes/DLL/2bc2w.png"))
    #返回识别结果
```

