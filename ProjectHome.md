# flash   ios ，iphone，android应用加载google admob广告 ane库 #
这个ane库使开发者能非常方便快捷的给跑在iphone android等的air手机应用中添加广告功能，获取收入。
本版本中包含了在iphone，ipad，android中使用的ane，所有平台都包含在一个ane中，这样跨平台，统一接口。
本lib可以在window上打包和调试，但是在pc上面不会显示广告，到真机上运行的时候会显示广告

## 下载 ##
最新版本下载地址:http://code.google.com/p/flash-air-admob-ane-for-ios/

admob网站: www.admob.com

要求最低air版本4.0,如果是在用flash cs 开发，记得升级air到4.0，flexbuilder也需要更新air到4.0以上。

ane编译版本基于 admob ios 6.8.0 and android 6.8.0。已经是最新版本，支持admob 新版本和新格式的admob ID格式。



最低要求  air sdk 4.0

## 使用本库只需要俩步 ##
使用方法:
1.添加如下代码在帧上或者类中
```
import so.cuo.platform.admob.Admob;
import so.cuo.platform.admob.AdmobPosition;


var admob:Admob=Admob.getInstance();//create a instance
admob.setKeys("a152834c2b8cce6");//set admob appid, banner and Interstitial  with the same id
//admob.setKeys("ca-app-pub-4744525099112098/453298989317","ca-app-pub-4744525099112098/453298989317");//set banner and Interstitial with different id admob.setKeys("banner id","Interstitial id");
admob.showBanner(Admob.BANNER,AdmobPosition.BOTTOM_CENTER);//show banner with relation position
```
2.
对于android开发.需要添加下面的东西到应用描述文件application-app.xml中。主要作用就是设定android最低版本，开启网络通信和添加admob的active，如果应用本来开启了这些功能，注意对比。
```
<android>
        <manifestAdditions><![CDATA[
			<manifest android:installLocation="auto">
			    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
			    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
			     <application>
			           <meta-data android:name="com.google.android.gms.version" android:value="4323000" />
			  	   <activity android:name="com.google.android.gms.ads.AdActivity" android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"/>
			     </application>
			</manifest>
		]]></manifestAdditions>
    </android>
```
3.注意在application-xml中的扩展标记，对于flash cs6和flash builder4.6以上版本添加ane后都会自动添加上这个标记，如果没有自动添加上的可以手动添加上
```
<extensions> <extensionID>so.cuo.platform.admob</extensionID> </extensions>
```








## 更多接口和功能 ##

1. admob广告事件的处理，包括广告点击后，广告接收到.

```
admob.addEventListener(AdEvent.onBannerReceive,onAdEvent);
```

2. 获得广告的尺寸信息，android平台必须在adreceived事件后才能获得真实的尺寸，对于smartbanner广告尺寸可能不是固定，请参考admob官方说明
```
protected function onAdReceived(event:AdmobEvent):void
{
if(event.type==AdmobEvent.onBannerReceive){
	trace(event.data.width,event.data.height);
}
}
```
3.获得ios或者android设备的屏幕像素尺寸
```
admob.getScreenSize()
```



### 6.6.7更新内容包括 ###

1.修改使用不同admob广告尺寸banner会奔溃的bug

2.修改全屏广告接收失败后将无法再请求广告bug


### 6.6.0本次更新内容包括: ###

1.包含ios 和android在一个包内

2.可以在pc上调试打包

3.更新 admob到6.6.7，不再使用udid

4.提供获取广告尺寸和设备尺寸的方法
### air 移动广告管理库 ###
[air-ad-network](http://code.google.com/p/adoble-flash-air-ad-network-framework/)

qq讨论群：56892018