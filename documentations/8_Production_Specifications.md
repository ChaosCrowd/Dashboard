本项目使用java作为后台开发语言，后台框架选取SpringMVC+MyBatis，故制定基本的java项目开发代码规范：

## **1、命名规范**
基本原则：
1）采用英文全称进行命名；
2）保持各层级名称基本统一；
3）命名英文单词用全称，避免用简称。

### 1.1 包命名规范

包名称必须全部用小写。
命名方式：com.域名.项目名称.项目模块.系统分层 
如：com.example.ordering.java.dao
       com.example.ordering.java.controller

### 1.2 类命名规范
类名以英文单词取名，使用大驼峰式命名法，首字母大写，多个英文单词以大写字母间隔，尽量避免使用缩写；类名中不允许‘_’、‘-’等特殊符号。

### 1.3 属性命名规范
a.定义属性的位置，在类定义的开始，按照public,protected,package,private顺序放置。

b.尽量用相同含义英文单词表示如：username。第一个字母小写，中间单词的第一个字母大写。不要用_或&等符号作为第一个字母。单字符的变量名一般只用于生命期非常短暂的变量。如：i,j,k,m,n一般用于int。如果变量是集合，则变量名应用复数，即以小写s结尾 。

c.常量属性：一律大写，单词间使用_分隔。例如：MAX_SIZE

### 1.4 方法命名规范
方法命名采用“动作+属性” 的方法。并且，动作以小写字母开始，属性以大写字母开始。常用的动作有：is、get、set、save、add、del等。示例：getName()

## **2.编码规范**
### 2.1 类及方法注释 
#### 2.1.1 类的注释 
目的：主要标注该类的作用，对类进行简单描述；记录类的作者和类的创建日期
```
/**
 * @Description 客户信息实体类
 * @author pony
 * @Date 2018.8.8 88:88:88
 * @version 1.0
 */
public class Customer {}
```
#### 2.1.2 方法的注释 
目的：描述该方法的主要意义；对方法的参数进行说明
```
/**
  * 
  * @Description 根据客户id,查询客户信息
  * @param customerId  客户id
  * @return 客户信息
  * @throws Exception
  */
public Customer getCustomerInfo(String customerId)throws Exception{
```

#### 2.1.3 属性的注释 
目的：描述该属性的意义.
```
/**
 * 用户姓名
 */
private String name;
```
或者
```
//用户姓名
private String name;
```

#### 2.1.4 代码段注释 
目的：行注释是一个非常短的注释，对当前代码片段进行解释说；行尾注释写在该代码块的上面； 
格式:
```
// 具体操作内容
customer.getName();

```

#### **2.1.5 Dao层、Service层接口、实现类的注释说明** 
Dao层、Service层接口中的方法都必须按照方法的注释要求进行注释
```
public interface IUserDetailDao extends IBaseDao<UserDetail> {

    /**
     * 获取成员列表
     * @author pony
     * @param page  分页
     * @param orgId ID
     * @return  成员列表
     */
    List<UserImpl> getList(Page page, Long orgId);
    
    /**
     * 列表查询
     * @author pony
     * @param page      分页  
     * @param content   关键字
     * @return
     */
    List<UserDetail> getList(Page page, String content);
```
Dao层、Service层**实现类**中的方法头部都不需要写注释，但在方法体中，如果写注释进行说明，则用//进行注释说明。 

#### 2.1.6 Entity的注释说明 
Entity中需要对每一个属性进行内容解释：
```
public class UserDetail extends BaseEntity implements  IUserDetail {

    //性别
    private String sex;         
    //备用电子邮箱
    private String email;
```

### 2.2 代码格式 
#### 2.2.1 格式缩进 
缩进：Tab键的标准占用字符为4个空格字符。 

#### 2.2.2 空白行 
逻辑上相关序代码与其前后之程序代码间应以空白行加以分隔；在注释段与程序段、以及不同程序段插入空行。 
每行只写一条语句。 

#### 2.2.3 行长度 
每行代码最多80个字符.

#### 2.2.4 定义与声明：

每个声明语句各成一行，如有特殊用途的可在后面加行尾注释.
正确示例：
```
int level;  // indentation level
int size;  // size of table
```
错误示例：
```
int level, size;
```
### 2.3 异常处理 
在当前的系统架构中，系统自上而下被分为控制器层、业务逻辑层、数据访问层、数据持久层、界面层。本规范约定各层的异常处理机制。

异常处理原则：

1、下层有常异，必须抛向上一层。 
2、为了使系统能够更好的跟踪运行情况，必须把底层异常放入新异常中。 
3、如果一个层要抛出多个异常，那么所有自定义异常必须统一继承一个父类异常。这样上层可以通过父类异常捕获。 
4、异常统一在控制器层处理，控制器层以下的层次在处理异常时，只需要把低层的异常类放到本层约定的异常类中，并抛出，如有需要可以加适当的异常消息。

### 2.4 对于业务逻辑复杂方法的处理约定 
如果一个方法业务逻辑比较复杂，在一个方法中进行处理，该方法将会臃肿、不宜阅读和维护，建议每个方法代码行不要大于50行，建议多使用方法重构。建议对方法中需要进行说明的地方进行注释，如参数、方法中多个步骤的业务逻辑处理。（备注，代码行数指的是代码语句行数，不是编辑器行数）

## 3. 其他规范

### 3.1 mysql数据库设计规范：
https://blog.csdn.net/sinat_29519243/article/details/70187040
