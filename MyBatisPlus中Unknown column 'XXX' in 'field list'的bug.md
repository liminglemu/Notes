# MyBatisPlus中Unknown column 'XXX' in 'field list'的bug



今天自己在搭项目的时候使用MyBatisPlus查询数据库的时候出现了一个我最无语的bug

![image-20230217194944976](https://raw.githubusercontent.com/liminglemu/PictureLibrary/main/image-20230217194944976.png)

上面写的很明白说id字段找不到，我先检查了我的sql语句，因为我使用的是@Select注解

![image-20230217195223590](https://raw.githubusercontent.com/liminglemu/PictureLibrary/main/image-20230217195223590.png)

第一个sql语句，我发现我好像没错误啊，实在想不懂哪里有问题，然后我就反复的检查model里的字段和数据库中是否一致

![image-20230217195113692](https://raw.githubusercontent.com/liminglemu/PictureLibrary/main/image-20230217195113692.png)

发现是完全一致的，中途也尝试了删除sql中id的查询条件，但是会报错，一样的Unknown column 'XXX' in 'field list'

最后我在控制台的sql打印语句中发现

![image-20230217195547936](https://raw.githubusercontent.com/liminglemu/PictureLibrary/main/image-20230217195547936.png)

is_deleted和from好像没有分开，我就去看了我的@Select中的sql语句，发现

![image-20230217195649747](https://raw.githubusercontent.com/liminglemu/PictureLibrary/main/image-20230217195649747.png)

确实少了一个空格只要在f前添加空格即可