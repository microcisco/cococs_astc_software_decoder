# cococs_astc_software_decoder

---
### 使用场景
只提供一份astc纹理在不支持astc的设备上自动解析成png从而减少包体和热更体积，使用的解析库是[astc-encoder](https://github.com/ARM-software/astc-encoder)
### 使用方法
直接覆盖对应的目录就行了，对应的版本是cocoscreate 2.4.13其他版本可以对应改一下
### 代码
```javascript
 if (Configuration::getInstance()->supportsASTC() == false)
    {
        //CCLOG("initWithASTCData: ERROR: Unsupported ASTC Compress texture on this device");
        //return false; 
        CCLOG("cocos2d: Hardware ASTC decoder not present. Using software decoder");
        png_res res = astcenc_main(0, {}, data, dataLen);
        return initWithPngData(res.png, res.len);
    }
```