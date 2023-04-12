![EE3 8B G8%8OQLE`4PX2GXI](https://user-images.githubusercontent.com/106834223/204996994-7dcf3b7b-2045-4f06-938d-ce8cf3737a51.png)

### Contact me
* **MyEmail:** hongbin666666@gmail.com
* **MyQQ:** 2623484066
* **wechat：**

![image](https://user-images.githubusercontent.com/106834223/229448163-a55896f0-3563-46c8-a4ba-77fefe0e9980.png)



```python
import pandas as pd
#读取北京地区信息
file_path_bj = open('C:/Users/Administrator/Desktop/北京地区信息.csv')
file_data_bjinfo = pd.read_csv(file_path_bj)
file_data_bjinfo

#读取天津地区信息
file_path_tj = open('C:/Users/Administrator/Desktop/天津地区信息.csv')
file_data_tjinfo = pd.read_csv(file_path_tj)
file_data_tjinfo

#检查file_data_bjinfo中的数据，返回True的表示是重复数据
file_data_bjinfo.duplicated()

#检测file_data_tjinfo中的数据，返回True的表示是重复与数据
file_data_tjinfo.duplicated()

#北京地区删除重复数据
file_data_bjinfo = file_data_bjinfo.drop_duplicates()
file_data_bjinfo

检测数据是否存在缺失
file_data_tjinfo.isnull()

#计算常驻人口的平均数，设置为float类型并保留两位小数
population = float("{:.2f}".format(
                      file_data_tjinfo['常住人口（万人）'].mean()))
#以字典映射的形式将需要填充的数据进行对应
values={'常住人口（万人）':population}
file_data_tjinfo = file_data_tjinfo.fillna(value=values)
file_data_tjinfo

#对北京地区信息进行异常值检测
%matplotlib inline
from pylab import mpl
mpl.rcParams['font.sans-serif']=['SimHei']
mpl.rcParams['axes.unicode_minus'] = False
file_data_bjinfo.boxplot(column=['行政面积（K㎡）',
                                '户籍人口（万人）','男性','女性','GDP（亿元）','常住人口（万人）'])

#对天津地区信息进行异常检测
%matplotlib inline
from pylab import mpl
mpl.rcParams['font.sans-serif']=['SimHei']
mpl.rcParams['axes.unicode_minus'] = False
file_data_tjinfo.boxplot(column=['行政面积（K㎡）',
                                '户籍人口（万人）','男性','女性','GDP（亿元）','常住人口（万人）'])

#对两地信息数据进行合并
pd.concat([file_data_bjinfo,file_data_tjinfo],
         ignore_index=True)
```
