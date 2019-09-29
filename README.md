# Hardcoder

[![license](http://img.shields.io/badge/license-BSD3-brightgreen.svg?style=flat)](https://github.com/Tencent/tinker/blob/master/LICENSE)[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/Tencent/tinker/pulls)



中文版请见[这里](./docs/README_chinese.md)。



**Hardcoder is a solution which allows Android APP and Android System to communicate with each other directly, solving the problem that Android APP could only use system standard API rather than the hardware resource of system. Through Hardcoder, Android APP could make good use of hardware resource of mobile phone such as CPU frequency, Large Core, GPU to improve APP performance while Android system could get more information from APP in order to provide system resource to Android APP more properly. At the same time, for lack of implementation by the standard interface, the APP and the system can also realize the model adaptation and function expansion through the framework.**



Hardcoder framework could averagely optimize the performance of Wechat by 10%-30% in terms of Wechat startup, video delivery, mini program startup, and other highly-loaded scenes. Furthermore, it could also averagely optimize the performance of Mobile QQ by 10%-50% in terms of mobile QQ startup, chatting Initialization, picture delivery, and other highly-loaded scenes. The framework now has been applied to mobile brands such as OPPO, vivo, Huawei, XIAOMI, Sumsang, Meizu, etc and covers more than 460 millions devices.  

![readme](./docs/images/readme.jpg)



## Getting started

1.  Read “[Product introduction of Hardcoder](./docs/hardcoder_introduction.md)” to learn about Hardcoder.

2. Read “[Technical introduction of Hardcoder](./docs/hardcoder_technology_introduction.md)” to know the implementation philosophy and technical framework.

3. Use the testapp to quickly verify the performance of Hardcoder. For the further detail, please check ”[Hardcoder testapp testing instruction](./docs/hardcoder_testapp_test_guide.md)“.

4. Please check the “[Hardcoder Application Instruction](./docs/hardcoder_users_guide.md)” to learn how to use Hardcoder.

   1. Download Hardcoder repo and compline Hardcoder aar.
   2. Apply Hardcoder aar to “build.gradle”.
   3. Call initHardCoder to establish socket connection when process initializes (Generally, it needs to request resource when process initializes. That is the reason why to call initHardCoder when process initializes). Every process is individual and they all need to call initHardCoder to establish socket connection. Every process keeps a socket after the connection and the socket will disconnect if the process quits.
   4. Call checkPermissin after the success of InitHardCoder call-back and transfer authentication values which are applied from different mobile brands by APP.
   5. Call startPerformance under the condition of resource request scenes and tranfer parameters that request resource. If the scene is in the stage of process initiation, for example APP startup, startPerformance should not be called until it successfully calls back initHardCoder or it needs to verify whether socket is connected by examining isConnect() of HardCoderJNI.
   6. Actively call stopPerformance when scene stops and it needs to transfer the “hashCode" corresponding to the startPerformance in order to identify the corresponding scene. Then it can stop this request.
   7. Test the performance. To do the comparison between the situation in which “Hardcoder is on and  off”.

5. Apply the authentication from mobile brands. For the further detail, please check [FAQ](./docs/FAQ.md).

6. Launch APP which has involved Hardcoder.

   

## Document Support

1. Product introduction of Hardcoder——https://github.com/Tencent/Hardcoder/blob/master/docs/hardcoder_introduction.md
2. Technical introduction of Hardcoder——https://github.com/Tencent/Hardcoder/blob/master/docs/hardcoder_technology_introduction.md
3. Hardcoder testapp testing instruction——https://github.com/Tencent/Hardcoder/blob/master/docs/hardcoder_testapp_test_guide.md
4. Hardcoder Application Instruction——https://github.com/Tencent/Hardcoder/blob/master/docs/hardcoder_users_guide.md
5. FAQ——https://github.com/Tencent/Hardcoder/blob/master/docs/FAQ.md




## License

Hardcoder is under the BSD license. See the [LICENSE](./LICENSE) file for details.



