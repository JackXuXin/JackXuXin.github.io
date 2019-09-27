# Mysql 联表查询
#博客
联表查询四种类型，inner join，left join，right join，full join。这四种类型是以join 的字段为基准的。我们以如下的表结构为例子。
学生表：
![](Mysql%20%E8%81%94%E8%A1%A8%E6%9F%A5%E8%AF%A2/22D92747-478C-474D-AC54-06639BE37EB9.png)
考试表：
![](Mysql%20%E8%81%94%E8%A1%A8%E6%9F%A5%E8%AF%A2/6BE4310E-3C22-40F8-9F18-D52F5AE1A4DA.png)
### inner join
可以理解为交集。这里的集合指的是关键字on后面标明的。例如：
`SELECT * FROM Student JOIN Test ON Student.id = Test.studentId;`这句话的意思是以Student中的id 和 Test中的studentId作为对应。现在，Student中包含ID的集合为{1,2,3}，Test中包含studentId的集合为{1,4}（实际上为{1，1，1，4}，因为集合需要去除重复项，所以就为{1,4}）。{1,2,3}^{1,4} = {1}。所以只包含id为1的结果。

![](Mysql%20%E8%81%94%E8%A1%A8%E6%9F%A5%E8%AF%A2/791488DC-F242-4ECC-BA08-53AF08FCF5B6.png)
### left join
以左边的表为准。也就是说左边的表中有的元素就一定会在结果集中出现，如果左边的表有，右边的表没有的行，右边的表的字段以null填充。例如：
`SELECT * FROM Student LEFT JOIN Test ON Student.id = Test.studentId;`现在，Student中包含ID的集合为{1,2,3}，Test中包含studentId的集合为{1,4}。以左边的表为准，也就是Student表为准，所以结果集中出现Student.id = {1,2,3}。id = 2，3时右边的表test中没有相关学生的成绩记录，所以id(1)，studentId，score都为NULL。
![](Mysql%20%E8%81%94%E8%A1%A8%E6%9F%A5%E8%AF%A2/DCEF5381-B3CE-438C-B8E4-3A622F33CFA8.png)
### right join
与left join相反，以右边的表为准，左边为空的记录，以NULL填充。
![](Mysql%20%E8%81%94%E8%A1%A8%E6%9F%A5%E8%AF%A2/D98360DB-E97F-43B2-9A55-23D275AE9265.png)