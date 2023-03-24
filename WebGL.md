Target Output: WebGL

# 1, 编译模板（导出webgl用的html模板）

Assets/WebGLTemplate

在此文件夹放置一个从官方复制的，修改其中内容。然后在Project Settings相关地方选择该模板，后面的输出就会使用该模板。

# 2, 供C#调用的js

plugins下放置*.jslib文件，格式从Unity官方文档中直接复制一个模板上改动即可。

# 3, js调用C#

核心：通过js中的unityInstance.SendMessage()，调用场景中指定GameObject上的脚本方法。通俗的说，就是在Gameobject上挂一个脚本，调用该Gameobject脚本中的方法。

为了方便使用，可使用window这个全局变量，把unityInstance缓存到该全局变量中，后面就可以用

window.unityInstance.SendMessage('CsharpGameobject', "MethodName", parameter)



