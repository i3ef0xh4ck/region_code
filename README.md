# 爬取最新全国区划和城乡划分代码

## 为方便使用，已导出sqlite数据库文件

![Alt text](./db2.jpg)

```
--查询sql
select a.tilte,a.level,b.total from (
select "province" as tilte,1 as level 
union select "city",2 
union select "county",3 
union select "town",4 
union select "village",5 order by level) as a
inner join (
select level,count(*) as total from region group by level) as b 
on a.level=b.level
union select '','',count(*) as total from region order by total

```
#### 查询结果统计

![Alt text](./db1.jpg)

- [sqlite数据库文件下载](https://github.com/godghdai/region_code/blob/master/store/database/region_code.zip)


## 18位身份证号解析
```
const { idcardParse } = require("./src/util/Idcard");
console.log(idcardParse("652822199402046016"))
```

#### 结果
```
{
    success: true,
    province: '新疆维吾尔自治区',
    city: '巴音郭楞蒙古自治州',
    county: '轮台县',
    birthday: '1994年02月04日',
    policeCode: 60,
    sex: '男',
    checkCode: '6'
}
```


## 如何使用

```
$ npm i
$ npm run start

F:\tjcode>npm run start
> node Start.js

北京市
北京市 -> 市辖区
北京市 -> 市辖区 -> 东城区
北京市 -> 市辖区 -> 东城区 -> 东华门街道办事处
北京市 -> 市辖区 -> 东城区 -> 景山街道办事处
北京市 -> 市辖区 -> 东城区 -> 交道口街道办事处
北京市 -> 市辖区 -> 东城区 -> 安定门街道办事处
北京市 -> 市辖区 -> 东城区 -> 北新桥街道办事处
北京市 -> 市辖区 -> 东城区 -> 东四街道办事处
北京市 -> 市辖区 -> 东城区 -> 朝阳门街道办事处
北京市 -> 市辖区 -> 东城区 -> 建国门街道办事处
北京市 -> 市辖区 -> 东城区 -> 东直门街道办事处
北京市 -> 市辖区 -> 东城区 -> 和平里街道办事处
北京市 -> 市辖区 -> 东城区 -> 前门街道办事处
北京市 -> 市辖区 -> 东城区 -> 崇文门外街道办事处
终止批处理操作吗(Y/N)?

```


## JSON下载链接
- [全国区划和城乡划分代码](https://github.com/godghdai/region_code/blob/master/data/%E8%A1%8C%E6%94%BF%E5%8C%BA%E5%88%92%E4%BB%A3%E7%A0%81.zip)
- [北京市](https://github.com/godghdai/region_code/blob/master/data/%E5%8C%97%E4%BA%AC%E5%B8%82.zip)
- [天津市](https://github.com/godghdai/region_code/blob/master/data/%E5%A4%A9%E6%B4%A5%E5%B8%82.zip)
- [河北省](https://github.com/godghdai/region_code/blob/master/data/%E6%B2%B3%E5%8C%97%E7%9C%81.zip)
- [山西省](https://github.com/godghdai/region_code/blob/master/data/%E5%B1%B1%E8%A5%BF%E7%9C%81.zip)
- [内蒙古自治区](https://github.com/godghdai/region_code/blob/master/data/%E5%86%85%E8%92%99%E5%8F%A4%E8%87%AA%E6%B2%BB%E5%8C%BA.zip)
- [辽宁省](https://github.com/godghdai/region_code/blob/master/data/%E8%BE%BD%E5%AE%81%E7%9C%81.zip)
- [吉林省](https://github.com/godghdai/region_code/blob/master/data/%E5%90%89%E6%9E%97%E7%9C%81.zip)
- [黑龙江省](https://github.com/godghdai/region_code/blob/master/data/%E9%BB%91%E9%BE%99%E6%B1%9F%E7%9C%81.zip)
- [上海市](https://github.com/godghdai/region_code/blob/master/data/%E4%B8%8A%E6%B5%B7%E5%B8%82.zip)
- [江苏省](https://github.com/godghdai/region_code/blob/master/data/%E6%B1%9F%E8%8B%8F%E7%9C%81.zip)
- [浙江省](https://github.com/godghdai/region_code/blob/master/data/%E6%B5%99%E6%B1%9F%E7%9C%81.zip)
- [安徽省](https://github.com/godghdai/region_code/blob/master/data/%E5%AE%89%E5%BE%BD%E7%9C%81.zip)
- [福建省](https://github.com/godghdai/region_code/blob/master/data/%E7%A6%8F%E5%BB%BA%E7%9C%81.zip)
- [江西省](https://github.com/godghdai/region_code/blob/master/data/%E6%B1%9F%E8%A5%BF%E7%9C%81.zip)
- [山东省](https://github.com/godghdai/region_code/blob/master/data/%E5%B1%B1%E4%B8%9C%E7%9C%81.zip)
- [河南省](https://github.com/godghdai/region_code/blob/master/data/%E6%B2%B3%E5%8D%97%E7%9C%81.zip)
- [湖北省](https://github.com/godghdai/region_code/blob/master/data/%E6%B9%96%E5%8C%97%E7%9C%81.zip)
- [湖南省](https://github.com/godghdai/region_code/blob/master/data/%E6%B9%96%E5%8D%97%E7%9C%81.zip)
- [广东省](https://github.com/godghdai/region_code/blob/master/data/%E5%B9%BF%E4%B8%9C%E7%9C%81.zip)
- [广西壮族自治区](https://github.com/godghdai/region_code/blob/master/data/%E5%B9%BF%E8%A5%BF%E5%A3%AE%E6%97%8F%E8%87%AA%E6%B2%BB%E5%8C%BA.zip)
- [海南省](https://github.com/godghdai/region_code/blob/master/data/%E6%B5%B7%E5%8D%97%E7%9C%81.zip)
- [重庆市](https://github.com/godghdai/region_code/blob/master/data/%E9%87%8D%E5%BA%86%E5%B8%82.zip)
- [四川省](https://github.com/godghdai/region_code/blob/master/data/%E5%9B%9B%E5%B7%9D%E7%9C%81.zip)
- [贵州省](https://github.com/godghdai/region_code/blob/master/data/%E8%B4%B5%E5%B7%9E%E7%9C%81.zip)
- [云南省](https://github.com/godghdai/region_code/blob/master/data/%E4%BA%91%E5%8D%97%E7%9C%81.zip)
- [西藏自治区](https://github.com/godghdai/region_code/blob/master/data/%E8%A5%BF%E8%97%8F%E8%87%AA%E6%B2%BB%E5%8C%BA.zip)
- [陕西省](https://github.com/godghdai/region_code/blob/master/data/%E9%99%95%E8%A5%BF%E7%9C%81.zip)
- [甘肃省](https://github.com/godghdai/region_code/blob/master/data/%E7%94%98%E8%82%83%E7%9C%81.zip)
- [青海省](https://github.com/godghdai/region_code/blob/master/data/%E9%9D%92%E6%B5%B7%E7%9C%81.zip)
- [宁夏回族自治区](https://github.com/godghdai/region_code/blob/master/data/%E5%AE%81%E5%A4%8F%E5%9B%9E%E6%97%8F%E8%87%AA%E6%B2%BB%E5%8C%BA.zip)
- [新疆维吾尔自治区](https://github.com/godghdai/region_code/blob/master/data/%E6%96%B0%E7%96%86%E7%BB%B4%E5%90%BE%E5%B0%94%E8%87%AA%E6%B2%BB%E5%8C%BA.zip)
