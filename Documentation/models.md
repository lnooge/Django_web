这是一篇介绍Django Model 的文章，再次记录以便往后查阅。
本文不属于Django_web项目文件，只是用来平常查阅相关资料只用。
https://github.com/lnooge/Django_web
这是我的Django项目，新手学习中！

# Field Options
** null 
   默认值为 Flase,设置Ture则字段可以为null

** blank 
   默认值为 Flase,设置为True则字段可以为空字符串

** choices
   枚举字段，用法：
   SHIRT_SIZES (
   ('S', 'Small'),
   ('M', 'Medium'),
   ('L', 'Large'),
   )

   shirt_size = models.CharField(max_length=1, choices=SHIRT_SIZES)
   
   "shirt_size="L" # 'S'\'M'\'L'

** default
   默认值，可以设方法

** help_text
   组件的help展示字段

** primary_key
   设为True则为主键，Django会默认生成自曾主键，一般可以不用

** unique
   设为True 则是唯一键
