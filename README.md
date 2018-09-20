#CatMeet_Android
因为资源有限，所以根据现有情况进行项目设计及注意事项

#1.代码规范 建议看一下项目中的codetarget文件，里面是阿里的java和android编码规范，可以借鉴参考
#2.代码注释模版
类：

/**
 * @ClassName: ${NAME}
 * @Description:
 * @author: ${USER}
 * @date: ${DATE}${TIME}
 */

 接口：
 /**
  * @InterfaceName: ${NAME}
  * @Description:
  * @author: ${USER}
  * @date: ${DATE}${TIME}
  */

 方法：（案例https://www.cnblogs.com/baron89/p/4668053.html）
 /**
  * @Description:
  * @author: $user$
  * @date: $date$ $time$
  */

 其他：
 /**
  * 内容   或 //内容
  */
#3.android工程的组件一般分为两种，lib组件和application组件，即所有lib组件为application组件服务，尽量避免lib与lib组件依赖关系
#4.架构设计进行中 此项目重心在于插件化开发、服务、广播、通知、内容提供者、音视频方向、即时通信方向得到锻炼，一些注意事项请参考阿里安卓规范文档并养成习惯
#5.项目下载  git clone --recursive git@git.coding.net:muwudi/CatMeet_Android.git
#6.目前先用submodule策略（https://www.jianshu.com/p/cbb302510811）维护公共组件库，未来当公共依赖库稳定了会上传jcenter发版，实现不同插件使用不同版本公共依赖库，已达到插件app完全独立效果,因为开发效率和维护成本问题，就不针对每个插件做定制化依赖，导致插件内存偏大，敬请谅解
#7.每个插件新增submodule后切记在工程当root settings.gradle手动加入 include ':app',':commonbase','commonhttp','commonui' 补充后3
#8.打包命令 在插件项目目录执行 ./gradlew clean assemblePlugin
#9.此命令测试应用冷启动时间 cd到项目目录利用终端命令（注意：mac系统需要对sdk环境变量配置，如不会配置请联系我）
#adb shell am start -S -W com.cat521.mbh/com.cat521.mbh.module.presenter.HostMainActivity 此命令测试应用启动时间 下面是当前测试
#ThisTime: 803（最后一个 Activity 的启动耗时）
#TotalTime: 803（启动一连串的 Activity 总耗时.(有几个Activity 就统计几个)）
#WaitTime: 809（应用进程的创建过程+TotalTime）
