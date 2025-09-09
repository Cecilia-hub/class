这个仓库中包含了我课程中做的一些小项目，其中文件夹单独列出来的部分是移动软件开发课程中的实验
目前实验一是制作一个简单小程序，实验二是制作一个天气查询小程序，实验三是微信小程序的云开发

# 实验 2：天气查询小程序       

## **一、实验目标**

1、学习使用快速启动模板创建小程序的方法；2、学习不使用模板手动创建小程序的方法。



## 二、实验步骤

列出实验的关键步骤、代码解析、截图。
### 1.准备工作
#### 1.1 API 密钥申请
由于实验所需的数据都来自和风天气，所以在进行实验前，我们首先要登录和风天气并进行注册

![alt text](1.png)

这里我们要点击免费注册

![alt text](2.png)

输入完信息注册完之后，我们会进入这个控制台

![alt text](3.png)

点击项目管理并创建项目后，我们可以看到这个界面

![alt text](4.png)

随后，我们可以添加凭证，并生成一个秘钥

![alt text](6.png)

#### 1.2 服务器域名配置

在此次实验中，需要用到外来网址进行访问数据，所以说我们需要点开微信小程序平台，添加我们可能要用到的网址

![alt text](8.png)

注意这个地方还需添加和风天气中我们账号的域名，后面直接用这些网站登录是无法访问数据的(可能是软件更注重隐私导致的)


### 2.项目创建
这部分内容和上次实验是一样的，我就不再赘述了，还是按照实验手册将模版调整好

![alt text](9.png)

### 3.页面配置
#### 3.1导航栏设计
导航栏部分我们需要更改颜色，并且需要修改标题

![alt text](10.png)

调整后结果是这样的

![alt text](11.png)

#### 3.2 页面设计
页面主要包括四个大部分：

picker组件，用于地区选择器

text组件，用于显示当前城市的温度和天气状况

image组件，用于显示当前城市的天气图标

view组件，用于分行显示湿度，气压等天气信息

##### 3.2.1 整体设计
首先设置整体容器，在.wxml文件中编改写代码：

![alt text](12.png)

随后在app.wxss中设置样式

![alt text](13.png)

##### 3.2.2 地区选择器
地区选择器使用picker组件来实现，wxml文件中：

![alt text](14.png)

效果如下图所示：

![alt text](15.png)

点击弹窗后可以更改地址：

![alt text](16.png)


##### 3.2.3 文本设计
wxml中加入以下代码：

![alt text](17.png)

在.wxss文件中我们要为文本设计对应的样式：

![alt text](18.png)

最终效果如图：

![alt text](19.png)

##### 3.2.4 图标设计
wxml中加入以下代码：

![alt text](20.png)

在.wxss文件中我们要为文本设计对应的样式：

![alt text](21.png)

最终效果如图：

![alt text](22.png)

##### 3.2.5 多行天气信息设计
wxml中加入以下代码：

![alt text](23.png)

在.wxss文件中我们要为文本设计对应的样式：

![alt text](24.png)

自此页面设计全部完成，最终效果如图：

![alt text](25.png)

#### 3.3  逻辑实现
##### 3.3.1 动态更新城市信息
首先我们需要修改picker组件中的北京市为{{region}}，将其设置为动态数据，同时为picker组件添加监听时间

.wxml中代码修改如下:

![alt text](26.png)

JS文件中也需要定义对应函数：

![alt text](27.png)

至此我们就可以切换国内的任意城市了

![alt text](28.png)

点击按钮后可以滑动

![alt text](29.png)

修改后可以显示别的城市

![alt text](30.png)

##### 3.3.2 动态获取天气数据
我们需要在JS文件中做出一些修改，首先是要获取天气数据时需要用到城市的ID号，然后利用查到的ID作为参数，再次调用和风天气的API来查询天气信息

![alt text](<屏幕截图 2025-08-26 124203.png>)

同时在生命周期函数中调用一次onLoad函数和自定义函数regionChange中分别调用一次该函数：
![alt text](31.png)

![alt text](32.png)

效果如下图：

![alt text](33.png)

切换地址后效果如下：

![alt text](34.png)

##### 3.3.3 更新页面信息
我们需要将所有需要更新的数据按照对应的名称修改：
![alt text](35.png)

最终效果如下：

![alt text](36.png)

切换地址后效果如下：

![alt text](90c4451489057ed72d800b5243503c8.png)
## 三、程序运行结果

列出程序的最终运行结果及截图。

![alt text](36.png)

可以看到，小程序现在已经能获取到不同城市的天气情况了。

![alt text](90c4451489057ed72d800b5243503c8.png)

## 四、问题总结与体会

描述实验过程中所遇到的问题，以及是如何解决的。有哪些收获和体会，对于课程的安排有哪些建议。

### 问题一：
在实验过程中，我遇到了无法访问城市ID以及天气状况网址的问题，经过排查，我猜测是由于用到网址是公开网址，而和风天气对于访问权限进行更严格设置的原因，所以我将原本网址替换为和风账号的域名，并且将这个网址上传到小程序的相应设置中，最终解决了这个问题。

### 问题二：
在实验过程中，我的图片突然无法正常显示了，检查了代码后，我发现这是因为我更改了images文件夹中的数据，导致数据是多层的，需要补全路径。

总的来说这次实验让我学习到了一些新的小程序制作技术，提高了我的学习兴趣，同时也让我更有成就感。

# 实验3：微信小程序云开发       

## **一、实验目标**

1、学习使用快速启动模板创建小程序的方法；2、学习不使用模板手动创建小程序的方法。



## 二、实验步骤

列出实验的关键步骤、代码解析、截图。

### 1. 准备工作

#### 1.1 创建微信小程序

由于之前的实验中完成过这一步，这里就不用赘述了。

#### 1.2 注册百度智能云

首先注册百度智能云账号，创建一个图像识别应用，并记录下相应的API key和secret key。

![alt text](<屏幕截图 2025-09-01 141545.png>)

![alt text](<屏幕截图 2025-09-01 145636.png>)

#### 1.3 创建一个云开发环境

通过微信小程序开发者工具创建一个云开发环境，注意记录自己的cloudid。

![alt text](<屏幕截图 2025-09-01 135210.png>)

### 2.项目运行

#### 2.1 项目导入

首先打开微信开发者工具导入垃圾分类小程序项目，注意这里需要导入整个文件夹。

![alt text](<屏幕截图 2025-09-01 135329.png>)

#### 2.2 修改相应ID或Key

##### 2.2.1 修改appID

在此处替换为自己的appID:

![alt text](<屏幕截图 2025-09-01 142826.png>)

##### 2.2.2 修改云空间ID

在此处替换为自己的云空间cloudid:

![alt text](<屏幕截图 2025-09-01 142336.png>)

##### 2.2.3 修改apisecret,apikey

在此处替换为自己的云空间apisecret,apikey:

![alt text](<屏幕截图 2025-09-01 143019.png>)

#### 2.3 部署云函数

点击cloudfuntions文件夹展开子文件夹，再依次右键点击展开的子文件夹并点击弹出的上传并部署：

![alt text](<屏幕截图 2025-09-01 143612.png>)

#### 2.4 部署云数据库

在云开发控制台点击数据库，创建集合trash, type后依次导入trash.json, type.json文件：

![alt text](<屏幕截图 2025-09-01 144203.png>)

最后部署就完成啦

## 三、程序运行结果

列出程序的最终运行结果及截图。

最终运行结果如下，可以看到在搜索栏搜索可以得到垃圾分类结果：

![alt text](<屏幕截图 2025-09-01 144514.png>)

![alt text](<屏幕截图 2025-09-01 144526.png>)

## 四、问题总结与体会

描述实验过程中所遇到的问题，以及是如何解决的。有哪些收获和体会，对于课程的安排有哪些建议。

### 问题一：
在导入开源代码后，开发者工具报错显示当前工具版本过低，我更新工具到最新版本后依然没有解决问题。

![alt text](<屏幕截图 2025-09-01 140248.png>)

后面在本地设置的调试基础库部分更换了版本后，终于解决了这个问题。

![alt text](<屏幕截图 2025-09-01 144501.png>)


总的来说这次实验还是非常顺利的，让我学习到了如何使用云开发功能，提高了我的学习兴趣，同时也让我对后面课设的设计多了一点思考。

# 实验四 制作视频播放小程序


## **一、实验目标**

1、学习使用快速启动模板创建小程序的方法；2、学习不使用模板手动创建小程序的方法。



## 二、实验步骤

列出实验的关键步骤、代码解析、截图。

### 1. 项目创建 

项目创建部分和之前的一样：

![alt text](<屏幕截图 2025-09-02 082958.png>)

### 2.页面配置

页面配置部分，前面部分和之前的实验是一致的，删除不需要的文件夹和文件，并生成自动函数模板。但是要注意的是，这里要新增一个pages文件夹，并把老师提供的图片复制进去。

![alt text](<屏幕截图 2025-09-02 083401.png>)

### 3.视图设计

#### 3.1 导航栏设计

首先更改导航栏的标题并设置背景颜色为金棕色，效果图和代码如下：

![alt text](<屏幕截图 2025-09-02 083657-1.png>)

#### 3.2 页面设计

页面区域主要分为视频播放器、弹幕发送区和视频列表这三个部分。

##### 3.2.1 视频播放器

wxml文件代码如下，设置组件：

![alt text](<屏幕截图 2025-09-02 084040.png>)

wxss文件代码如下，进行组件的相关设计：

![alt text](<屏幕截图 2025-09-02 084058.png>)

##### 3.2.2 弹幕发送区

wxml文件代码如下：

![alt text](<屏幕截图 2025-09-02 084213.png>)

wxss文件代码如下，分别对弹幕区域，文本输入框，按钮样式进行设置：

![alt text](<屏幕截图 2025-09-02 084242.png>)

效果图如下：

![alt text](<屏幕截图 2025-09-02 084253.png>)

##### 3.2.3 视频列表

视频列表部分，wxml文件代码如下：

![alt text](<屏幕截图 2025-09-02 084319.png>)

相应的wxss文件代码如下：

![alt text](<屏幕截图 2025-09-02 105713.png>)

效果图如下：

![alt text](<屏幕截图 2025-09-02 084348.png>)

###  4. 逻辑实现 

#### 4.1 更新播放列表

对wxml文件做如下修改：

![alt text](<屏幕截图 2025-09-02 084453.png>)

js文件中的data属性中加入list的内容，用于储存视频信息：

![alt text](<屏幕截图 2025-09-02 084540.png>)

效果如下：

![alt text](<屏幕截图 2025-09-02 084630.png>)

#### 4.2  点击播放视频

wxml文件中代码修改如下：

![alt text](<屏幕截图 2025-09-02 094056.png>)

随后在js文件的onload函数中创建视频上下文：

![alt text](<屏幕截图 2025-09-02 094120.png>)

随后在js文件中定义 playvideo函数：

![alt text](<屏幕截图 2025-09-02 094139.png>)

效果图如下：

![alt text](<屏幕截图 2025-09-02 094042.png>)

#### 4.3   发送弹幕 

wxml文件中，首先对区域一中的video组件做修改：

![alt text](<屏幕截图 2025-09-02 094324.png>)

随后在区域二中，对文本框追加弹幕输入属性：

![alt text](<屏幕截图 2025-09-02 094423.png>)

在js文件中增加这两个函数：

![alt text](<屏幕截图 2025-09-02 094818.png>)

效果图如下，可以发送红色的弹幕：

![alt text](<屏幕截图 2025-09-02 095005.png>)

要想生成不同颜色的彩色弹幕，我们可以在js文件中增加一个随机弹幕颜色函数：

![alt text](<屏幕截图 2025-09-02 095158.png>)

前面弹幕颜色部分的代码也要进行修改：

![alt text](<屏幕截图 2025-09-02 095205.png>)

## 三、程序运行结果

列出程序的最终运行结果及截图。

最终运行结果如下，视频播放过程中可以发送不同颜色的彩色弹幕：

![alt text](<屏幕截图 2025-09-02 095418.png>)

![alt text](<屏幕截图 2025-09-02 095428.png>)

## 四、问题总结与体会

描述实验过程中所遇到的问题，以及是如何解决的。有哪些收获和体会，对于课程的安排有哪些建议。

### 问题一：
这次实验总的来说还是非常顺利的，但是在创建images文件夹的时候一定要注意文件夹的位置是和pages等并列的，有的时候没注意看，可能会创建到某个文件夹下，这样就会出错。

此次实验中我学习了如何制作一个视频播放小程序，觉得收获匪浅，希望在日后能继续学习微信小程序的制作，更加精益求精。

# 实验五：第一个 HarmonySO 应用 

## **一、实验目标**

通过这一部分内容的学习和初步实践，开发者可以快速构建出首个HarmonyOS应用，掌握应用程序包结构、资源文件的使用以及ArkTS的核心功能和语法等基础知识，为后续的应用开发奠定基础。

## 二、实验步骤

列出实验的关键步骤、代码解析、截图。

### 1. 准备工作

#### 1.1 工具准备

在进行实验之前，首先要准备好实验工具，下载并安装最新版DevEco Studio。

![alt text](<屏幕截图 2025-09-08 111246.png>)

#### 1.2 创建ArkTS工程

若首次打开DevEco Studio，则单击Create Project创建工程；如果已经打开了一个工程，在菜单栏选择File > New > Create Project来创建一个新工程。选择Application应用开发，选择模板Empty Ability，单击Next进行下一步配置。

以下是工程配置界面，Compatible SDK表示兼容的最低API Version

![alt text](<屏幕截图 2025-09-08 111154.png>)

点击finish，工程就创建完成啦，出现以下界面：

![alt text](<屏幕截图 2025-09-08 111212.png>)

### 2. 构建第一个页面

#### 2.1 使用文本组件

工程同步完成后，在Project窗口，单击entry > src > main > ets> pages，打开Index.ets文件，将页面从RelativeContainer相对布局修改成Row/Column线性布局。

Index.ets文件的示例如下：

![alt text](<屏幕截图 2025-09-08 133842.png>)

```Javascript
// Index.ets
 @Entry
 @Component
 struct Index {
 @State message: string = 'Hello World';
 build() {
 Row() {
 Column() {
 Text(this.message)
 .fontSize(50)
 .fontWeight(FontWeight.Bold)
 }
 .width('100%')
    }
    .height('100%')
  }
 }
```

#### 2.2 添加按钮

在默认页面基础上，我们添加一个Button组件，作为按钮响应用onClick事件，从而实现跳转到另一个页面。Index.ets文件的示例如下，点击右上角的preview即可看到效果：

![alt text](<屏幕截图 2025-09-08 134024.png>)

```Javascript
// Index.ets
// Index.ets
 @Entry
 @Component
 struct Index {
  @State message: string = 'Hello World';
  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
        // 添加按钮，以响应用户onClick事件
        Button() {
          Text('Next')
            .fontSize(30)
            .fontWeight(FontWeight.Bold)
        }
        .type(ButtonType.Capsule)
        .margin({
          top: 20
        })
        .backgroundColor('#0D9FFB')
        .width('40%')
        .height('5%')
      }
      .width('100%')
    }
    .height('100%')
  }
 }

```

### 2.构建第二个页面

#### 2.1 创建第二个页面

首先在Project窗口，打开entry > src > main > ets，右键单pages文件夹，选择New > ArkTS File，命名为Second，单击回车键。

![alt text](<屏幕截图 2025-09-08 134153.png>)

接下来配置第二个页面的路由，在Project窗口，打开entry > src >main > resources > base > profile，在main_pages.json文件中的"src"下配置第二个页面的路由"pages/Second"。

![alt text](<屏幕截图 2025-09-08 134247.png>)

#### 2.2 添加文本及按钮

参照第一个页面，在第二个页面添加Text组件、Button组件等，并设其样式。
Second.ets文件的示例如下：

```Javascript
// Second.ets
@Entry
@Component
struct Second {
  @State message: string = 'Hi there';
  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
        Button() {
          Text('Back')
            .fontSize(30)
            .fontWeight(FontWeight.Bold)
        }
        .type(ButtonType.Capsule)
        .margin({
          top: 20
        })
        .backgroundColor('#0D9FFB')
        .width('40%')
        .height('5%')
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

效果图如下：
![alt text](<屏幕截图 2025-09-08 134413.png>)

### 3 实现页面间的跳转

页面间的导航可以通过页面路由router来实现。页面路由router根据面url找到目标页面，从而实现跳转。使用页面路由请导入router模块。

#### 3.1 第一个页面跳转到第二个页面

在第一个页面中，跳转按钮绑定onClick事件，单击按钮时跳转到第二页。Index.ets文件的示例如下：

```Javascipt
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';
@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
        // 添加按钮，以响应用户onClick事件
        Button() {
          Text('Next')
            .fontSize(30)
            .fontWeight(FontWeight.Bold)
        }
        .type(ButtonType.Capsule)
        .margin({
          top: 20
        })
        .backgroundColor('#0D9FFB')
        .width('40%')
        .height('5%')
        // 跳转按钮绑定onClick事件，单击时跳转到第二页
        .onClick(() => {
          console.info(`Succeeded in clicking the 'Next' button.`)
          // 获取UIContext
          let uiContext: UIContext = this.getUIContext();
          let router = uiContext.getRouter();
          // 跳转到第二页
          router.pushUrl({ url: 'pages/Second' }).then(() => {
            console.info('Succeeded in jumping to the second page.')
          }).catch((err: BusinessError) => {
            console.error(`Failed to jump to the second page. Code is ${err.code},
message is ${err.message}`)
          })
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

效果图如下，点击按钮后可以跳转到第二个页面：

![alt text](<屏幕截图 2025-09-08 134545.png>)

#### 3.2 第二个页面返回到第一个页面

在第二个页面中，返回按钮绑定onClick事件，单击按钮时返回到第一页。Second.ets文件的示例如下：

```Javascript
// Second.ets
import { BusinessError } from '@kit.BasicServicesKit';
@Entry
@Component
struct Second {
  @State message: string = 'Hi there';
  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
        Button() {
          Text('Back')
            .fontSize(30)
            .fontWeight(FontWeight.Bold)
        }
        .type(ButtonType.Capsule)
        .margin({
          top: 20
        })
        .backgroundColor('#0D9FFB')
        .width('40%')
        .height('5%')
        // 返回按钮绑定onClick事件，单击按钮时返回到第一页
        .onClick(() => {
          console.info(`Succeeded in clicking the 'Back' button.`)
          // 获取UIContext
          let uiContext: UIContext = this.getUIContext();
          let router = uiContext.getRouter();
          try {
            // 返回第一页
            router.back()
            console.info('Succeeded in returning to the first page.')
          } catch (err) {
            let code = (err as BusinessError).code;
            let message = (err as BusinessError).message;
            console.error(`Failed to return to the first page. Code is ${code},message is ${message}`)
          }
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

效果图如下，点击next按钮到后面一个页面之后，点击back又可以回到前面一个页面：

![alt text](<屏幕截图 2025-09-08 134721.png>)

### 4. 使用真机运行应用

1. 将搭载HarmonyOS系统的真机与电脑连接。
2. 单击File > Project Structure... > Project >SigningConfigs界面勾选Support HarmonyOS和Automatically generate signature，单击界面提示的Sign In，使用华为账号登录。等待自动签名完成后，单击OK即可。如下图所示：

![alt text](<屏幕截图 2025-09-08 135110.png>)

## 三、程序运行结果

列出程序的最终运行结果及截图。

最终运行结果如下，可以点击跳转到下一页，然后再跳转回上一页：

![alt text](<屏幕截图 2025-09-08 134545-1.png>)

![alt text](<屏幕截图 2025-09-08 134721-1.png>)

## 四、问题总结与体会

描述实验过程中所遇到的问题，以及是如何解决的。有哪些收获和体会，对于课程的安排有哪些建议。

此次实验我基本上没有遇到什么问题，全程都是按照老师提供的手册和代码来的。经过这次实验，我制作了我的首个HarmonyOS应用，了解了应用程序包结构、资源文件的使用以及ArkTS的核心功能和语法等基础知识，这为我后续的开发提供了基础。

# 实验六：推箱子游戏  


## **一、实验目标**

1、综合应用所学的知识创建完整的推箱子游戏；2、熟练掌握canvas和绘图API。

## 二、实验步骤

列出实验的关键步骤、代码解析、截图。

### 1. 准备工作

#### 1.1 项目创建

项目创建部分和之前的一样，这里就不赘述了：

![alt text](<屏幕截图 2025-09-08 222516.png>)

#### 1.2 页面配置

页面配置部分，前面部分和之前的实验是一致的，删除不需要的文件夹和文件，并生成自动函数模板。但是要注意的是，这里要新增一个images文件夹，并把老师提供的图片复制进去。

![alt text](<屏幕截图 2025-09-08 222959.png>)

随后还要新增一个utils文件夹，新建一个data.js文件：

![alt text](<屏幕截图 2025-09-08 223046.png>)

### 2.页面设计

#### 2.1 导航栏设计

将导航栏背景颜色改为珊瑚红色，字体改为白色：

![alt text](<屏幕截图 2025-09-08 223410.png>)

```Javascript
"window": {
    "navigationBarBackgroundColor": "#E64340",
    "navigationBarTitleText": "推箱子游戏"
  },
```

效果图如下：

![alt text](<屏幕截图 2025-09-08 223806.png>)

#### 2.2 公共样式设计

首先在app.wxss中设置页面容器和顶端标题的公共样式：

![alt text](<屏幕截图 2025-09-08 223956.png>){: width="50%"}

```Javascript
.container{
  height: 100vh;
  color: #E64340;
  font-weight: bold;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
}
.title{
  font-size: 18pt;
}
```

#### 2.3 首页设计

首页要设计的包含标题和关卡列表，在wxml文件中写入下列代码：

![alt text](<屏幕截图 2025-09-08 224025.png>)

```Javascript
<view class='container'>
  <view class='title'>游戏选关</view>
  <view class='levelBox'>
    <view class="box">
      <image src="/images/level01.png"/>
      <text>第一关</text>
    </view>
  </view>
</view>
```

在wxss文件中添加相应样式：

![alt text](<屏幕截图 2025-09-08 224045.png>)

```Javascript
.levelBox{
  width: 100%;
}
.box{
  width: 50%;
  float: left;
  margin: 20rpx 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}
image{
  width: 300rpx;
  height: 300rpx;
}
```

效果图如下：

![alt text](<屏幕截图 2025-09-08 224116.png>){: width="50%"}

#### 2.4 游戏页面设计

由于暂时还没有做点击跳转的设计，所以可以先添加一个编译模式，来编译game页面：

![alt text](<屏幕截图 2025-09-08 224352.png>){: width="50%"}

然后要在pages文件夹下新增game文件夹，并新建相应的四个文件：

![alt text](<屏幕截图 2025-09-08 225353.png>)

游戏页面共有四个组成部分：标题，游戏区域，方向键和重新开始按钮。在wxml中写入以下代码：

![alt text](<屏幕截图 2025-09-08 224554.png>)

```Javascript
<view class='container'>
  <view class='title'>第一关</view>
  <canvas canvas-id="myCanvas"/>
  <view class='btnBox'>
    <button type="warn">↑</button>
    <view>
      <button type="warn">←</button>
      <button type="warn">↓</button>
      <button type="warn">→</button>
    </view>
  </view>
  <button type="warn">重新开始</button>
</view>

```

在wxss中设置样式：

![alt text](<屏幕截图 2025-09-08 224622.png>)

```Javascript
canvas{
  border: 1rpx solid;
  width: 320px;
  height: 320px;
}
.btnBox{
  display: flex;
  flex-direction: column;
  align-items: center;
}
.btnBox view{
  display: flex;
  flex-direction: row;
}
.btnBox button{
  width: 90rpx;
  height: 90rpx;
}
button{
  margin: 10rpx;
}
```

注意这里新增了game页面，一定要在app.json文件中声明：

![alt text](<屏幕截图 2025-09-08 224825.png>)

效果如下：

![alt text](<屏幕截图 2025-09-08 225539.png>){: width="50%"}

### 3. 逻辑实现

#### 3.1 公共逻辑

utils文件下的data.js文件是用于存储游戏的地图数据等公共数据，在其中写入以下代码，其中，地图中1代表墙，2代表道路，3代表终点，4代表箱子，5代表人物，6代表地图外围。：

![alt text](<屏幕截图 2025-09-08 225612.png>)

```Javascript
var map1 = [
  [0,1,1,1,1,1,0,0],
  [0,1,2,2,1,1,1,0],
  [0,1,5,4,2,2,1,0],
  [1,1,1,2,1,2,1,1],
  [1,3,1,2,1,2,2,1],
  [1,3,4,2,2,1,2,1],
  [1,3,2,2,2,4,2,1],
  [1,1,1,1,1,1,1,1]
]
var map2 = [
  [0,0,1,1,1,0,0,0],
  [0,0,1,3,1,0,0,0],
  [0,0,1,2,1,1,1,1],
  [1,1,1,4,2,4,3,1],
  [1,3,2,4,5,1,1,1],
  [1,1,1,1,4,1,0,0],
  [0,0,0,1,3,1,0,0],
  [0,0,0,1,1,1,0,0]
]
var map3=[
  [0,0,1,1,1,1,0,0],
  [0,0,1,3,3,1,0,0],
  [0,1,1,2,3,1,1,0],
  [0,1,2,2,4,3,1,0],
  [1,1,2,2,5,4,1,1],
  [1,2,2,1,4,4,2,1],
  [1,2,2,2,2,2,2,1],
  [1,1,1,1,1,1,1,1]
]
var map4=[
  [0,1,1,1,1,1,1,0],
  [0,1,3,2,3,3,1,0],
  [0,1,3,2,4,3,1,0],
  [1,1,1,2,2,4,1,1],
  [1,2,4,2,2,4,2,1],
  [1,2,1,4,1,1,2,1],
  [1,2,2,2,5,2,2,1],
  [1,1,1,1,1,1,1,1]
]
module.exports={
  maps:[map1,map2,map3,map4]
}
```

这样就完成了公共部分的逻辑处理，之后需要在其他页面中引用该文件，在game.js页面的顶部添加以下代码：

![alt text](<屏幕截图 2025-09-08 230110.png>)

```Javascript
canvas{
var data=require('../../utils/data.js')
```

#### 3.2 首页逻辑

##### 3.2.1 关卡列表展示

接下来要在js文件的data中录入关卡图片的信息：

![alt text](<屏幕截图 2025-09-08 230145.png>)

```Javascript
data: {
    levels:[
      'level101.png',
      'level102.png',
      'level103.png',
      'level104.png',
    ]
  },
```

随后对wxml文件也做出修改：

![alt text](<屏幕截图 2025-09-08 230213.png>)


```Javascript
<view class="box" wx:for="{{levels}}" wx:key="levels{{index}}">
      <image src="/images/{{item}}"/>
      <text>第{{index+1}}关</text>
```

效果图如下：

![alt text](<屏幕截图 2025-09-08 230256.png>){: width="50%"}

##### 3.2.2 点击跳转游戏界面

继续修改.wxml文件，为按钮添加点击事件，实现点击后跳转关卡的功能：

![alt text](<屏幕截图 2025-09-09 084043.png>)

```Javascript
  <view class="box" wx:for="{{levels}}" wx:key="levels{{index}}" bind:tap="chooseLevel" data-level='{{index}}'>
```
随后在js文件中添加相应的函数：

![alt text](<屏幕截图 2025-09-09 084133.png>)

```Javascript
chooseLevel:function(e){
  let level = e.currentTarget.dataset.level
  wx.navigateTo({
    url: '../game/game?level='+level,
  })
},
```

随后可以验证一下效果，点击首页的图标：

![alt text](<屏幕截图 2025-09-09 084216.png>){: width="50%"}

就可以跳转到相应的关卡：

![alt text](<屏幕截图 2025-09-09 084222.png>){: width="50%"}

#### 3.3 游戏页逻辑

##### 3.3.1 显示当前第几关

首先我们需要加入level数据，来显示当前游戏为第几关，然后在data内加入level属性，并且在OnLoad函数中接受跳转页面时传递来的参数，使用setData将level设置为接受到的参数。

在game.js文件中做出如下修改：

![alt text](<屏幕截图 2025-09-09 084551.png>)

```Javascript
onLoad(options) {
    let level=options.level
    this.setData({
      level:parseInt(level)+1
    })
  },
```

随后修改.wxml文件，使其动态显示关卡数：

![alt text](<屏幕截图 2025-09-09 084626.png>)

```Javascript
<view class='title'>第{{level}}关</view>
```

此时点击不同关卡就可以跳到不同的关卡页面了：

![alt text](<屏幕截图 2025-09-09 084649.png>){: width="50%"}

![alt text](<屏幕截图 2025-09-09 084703.png>){: width="50%"}

##### 3.3.2 游戏逻辑实现

首先在game.js文件中设置一些初始数据：

![alt text](<屏幕截图 2025-09-09 090351.png>)

```Javascript
var map=[
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0]
]
var box=[
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0],
  [0,0,0,0,0,0,0,0]
]
var w=40
var row=0
var col=0
```

随后在js文件中添加一个初始化函数，用来读取地图数据;

![alt text](<屏幕截图 2025-09-09 090428.png>)

```Javascript
initMap:function(level){
    let mapData=data.maps[level]
    for(var i=0;i<8;i++){
      for(var j=0;j<8;j++){
        box[i][j]=0
        map[i][j]=mapData[i][j]
        if(mapData[i][j]==4){
          box[i][j]=4
          map[i][j]=2
        }else if(mapData[i][j]==5){
          map[i][j]=2
          row=i
          col=j
        }
      }
    }
  },

```

然后添加一个绘制画布的函数：

![alt text](<屏幕截图 2025-09-09 091301-1.png>)

```Javascript
drawCanvas:function(){
    let ctx=this.ctx
    ctx.clearRect(0,0,320,320)
    for(var i=0;i<8;i++){
      for(var j=0;j<8;j++){
        let img='ice'
        if(map[i][j]==1){
          img='stone'
        }else if(map[i][j]==3){
          img='pig'
        }
        ctx.drawImage('/images/icons'+img+'.png',j*w,i*w,w,w)
        if(box[i][j]==4){
          ctx.drawImage('/images/icons/box.png',j*w,i*w,w,w)
        }
      }
    }
    ctx.drawImage('/images/icons/bird.png',col*w,row*w,w,w)
    ctx.draw()
  },
```

最后只需在OnLoad函数中依次调用自定义的函数，即可实现整个游戏地图的加载和绘制：

![alt text](<屏幕截图 2025-09-09 090529-1.png>)

```Javascript
onLoad(options) {
    let level=options.level
    console.log(options.level)
    this.setData({
      level:parseInt(level)+1
    })
    this.ctx=wx.createCanvasContext('myCanvas')
    this.initMap(level)
    this.drawCanvas()
  },
```

可以看到此时画布上的效果，以及出现了完整版的地图和图标：

![alt text](<屏幕截图 2025-09-09 091254.png>){: width="50%"}

#### 3.3.3 方向键逻辑设计

首先要为四个方向键添加点击事件：

![alt text](<屏幕截图 2025-09-09 091534.png>)

```Javascript
<button type="warn" bind:tap="up">↑</button>
<button type="warn" bind:tap="left">←</button>
      <button type="warn" bind:tap="down">↓</button>
      <button type="warn" bind:tap="right">→</button>
```

然后js文件中添加对应的函数，来实现人物的移动：

![alt text](<屏幕截图 2025-09-09 091700.png>)

```Javascript
up:function(){
    if(row>0){
      if(map[row-1][col]!=1 && box[row-1][col]!=4){
        row=row-1
      }
      else if(box[row-1][col]==4){
        if(row-1>0){
          if(map[row-2][col]!=1&&box[row-2][col]!=4){
            box[row-2][col]=4
            box[row-1][col]=0
            row=row-1
          }
        }
      }
      this.drawCanvas()
    }
  },
  down:function(){
    if(row<7){
      if(map[row+1][col]!=1 && box[row+1][col]!=4){
        row=row+1
      }
      else if(box[row+1][col]==4){
        if(row+1<7){
          if(map[row+2][col]!=1&&box[row+2][col]!=4){
            box[row+2][col]=4
            box[row+1][col]=0
            row=row+1
          }
        }
      }
      this.drawCanvas()
    }
  },
  left:function(){
    if(col>0){
      if(map[row][col-1]!=1 && box[row][col-1]!=4){
        col=col-1
      }
      else if(box[row][col-1]==4){
        if(col-1>0){
          if(map[row][col-2]!=1&&box[row][col-2]!=4){
            box[row][col-2]=4
            box[row][col-1]=0
            col=col-1
          }
        }
      }
      this.drawCanvas()
    }
  },
​
  right:function(){
    if(col<7){
      if(map[row][col+1]!=1 && box[row][col+1]!=4){
        col=col+1
      }
      else if(box[row][col+1]==4){
        if(col+1<7){
          if(map[row][col+2]!=1&&box[row][col+2]!=4){
            box[row][col+2]=4
            box[row][col+1]=0
            col=col+1
          }
        }
      }
      this.drawCanvas()
    }
  },
```

效果如下，可以看到人物的移动：

![alt text](<屏幕截图 2025-09-09 091854.png>){: width="50%"}

![alt text](<屏幕截图 2025-09-09 091905.png>){: width="50%"}

#### 3.4 判断游戏成功

在js文件里设置isWin函数，来判断游戏是否已经成功了：

![alt text](<屏幕截图 2025-09-09 091950.png>)

```Javascript
isWin:function(){
    for(var i=0;i<8;i++){
      for(var j=0;j<8;j++){
        if(box[i][j]==4&&map[i][j]!=3){
          return false
        }
      }
    }
    return true
  },
```

之后继续添加函数，调用判断函数并弹出提示框：

![alt text](<屏幕截图 2025-09-09 092014.png>)

```Javascript
checkWin:function(){
    if(this.isWin()){
      wx.showModal({
        title: '恭喜',
        content: '游戏成功',
        showCancel:false
      })
    }
  },
```

注意最后在方向键的每个函数设置中均需增加调用函数语句：

```Javascript
this.checkWin()
```

效果图如下：
![alt text](<屏幕截图 2025-09-09 092535.png>){: width="50%"}

#### 3.5 重新开始游戏

首先需要为重新开始按钮添加响应事件：

![alt text](<屏幕截图 2025-09-09 092602.png>)

```Javascript
<button type="warn" bind:tap="restartGame">重新开始</button>
```

随后增加相关函数：

![alt text](<屏幕截图 2025-09-09 092626.png>)

```Javascript
restartGame:function(){
    this.initMap(this.data.level-1)
    this.drawCanvas()
  },
```

这样，这次实验就圆满完成了。

## 三、程序运行结果

列出程序的最终运行结果及截图。

最终小程序效果如下，首先进入首页：

![alt text](<屏幕截图 2025-09-09 092641.png>){: width="50%"}

然后通过点击可以进入各个关卡：

![alt text](<屏幕截图 2025-09-09 092647.png>){: width="50%"}

进行游戏并成功后会弹出弹窗：

![alt text](<屏幕截图 2025-09-09 092717.png>){: width="50%"}

点击重新开始后又会恢复原本的游戏页面：

![alt text](<屏幕截图 2025-09-09 092725.png>){: width="50%"}

## 四、问题总结与体会

描述实验过程中所遇到的问题，以及是如何解决的。有哪些收获和体会，对于课程的安排有哪些建议。

### 问题一

首先，在定义一个新的页面的时候，我们应该在app.json文件中做好相应的定义不然会报错，除此之外，如果页面编译后没有出现相关页面，而是显示一行文件路径，那就说明是你的文件新增和文件位置有问题，可以多检查一下文件的位置关系。

### 问题二

其次，注意要在方向键功能定义函数的最后调用checkWin函数才能实现想要的功能，我一开始没有注意这一点，就走了一些弯路。

### 问题三

在编写markdown实验报告的时候，我也遇到一点问题，代码部分的```英文输入法下的，···是中文输入法下的反引号，是不适用的。

此次实验中我学习了如何制作一个推箱小游戏，这让我对于制作微信小程序有了一个更为清晰的了解，觉得收获匪浅，希望在日后能继续学习微信小程序的制作，更加精益求精。


