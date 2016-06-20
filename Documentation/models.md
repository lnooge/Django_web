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

** on_delete

# 实体间的关系
## 外键
   ForeignKey()

## 多对多
   ManyToManyField()

# Django之外键删除
   Django还是采用级联的删除方式，当你删除一个外键的是侯，外键关联的实体也被删除，但在创建models的时候，外键增加了一个可选的参数on_delete
   class Blog(models.Model):
       user = models.ForeignKey(User,blank=True,null=True,on_delete=models.SET_NULL)

   当blog对应的user删除时，blog里的user字段会设置为空值，而不是连同blog也删除掉。
   on_delete有多少个选项呢：
   1. CASCADE:这是默认的选项，练级删除，你无需显性指定它。
   2. PROTECT:保护模式，如果采用该选项，删除的时候，会抛出ProtectedError错误。
   3. SET_NULL: 置空模式，删除的时候，外键字段被置为空，前提就是blank=True,null=True,定义该字段的时候，允许为空。
   4. SET:自定义一个值，该值当然只能是对应的实体了，看一下代码：
   def get_sentinel_user():  
       return User.objects.get_or_create(username='deleted')[0]  
  
   class MyModel(models.Model):  
       user = models.ForeignKey(User, on_delete=models.SET(get_sentinel_user))
