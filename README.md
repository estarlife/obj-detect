tinymind运行地址：https://www.tinymind.com/executions/almdjgx6
一、protoc使用
1.在Linux下没有问题，需要注意路径，运行时需要在research目录下进行，因为object_detection/protos里面的proto文件里都写死了路径“object_detection/protos”
```
import "object_detection/protos/grid_anchor_generator.proto";
import "object_detection/protos/ssd_anchor_generator.proto";
```
2.在windows下使用须知
版本：proto3.4亲测有效，使用路径同上“models/research”
而proto3.5 proto3.6都会出错
```
object_detection/protos/*.proto: No such file or directory
```
![图片.png](https://upload-images.jianshu.io/upload_images/15517405-d95a63f608739671.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这程序像网友说得一样。。。比较dumb
二、模型
开始使用MODEL ZOO时并不知道究竟要用里面的什么文件，通过这次实验，基本上用的就是model.ckpt.meta，model.ckpt.index和model.ckpt.data-00000-of-00001,frozen*是冻结数据用来做inference的，所以数据集里传这三个就行了
不过saved model文件夹里的pb文件还不清楚做什么，再回头看看视频
三、数据集生成
代码中还需求一个trainval.txt，是用来提取图像和相应XML文件名列表的，可以自己手工生成一个。