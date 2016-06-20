* Django models Field 字段
# CharField(max_length=20) 字符型字段
# ForeignKey(Tag, on_delete=models.CASCADE) 外键字段
  1. on_delete 属性
     1. 



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
