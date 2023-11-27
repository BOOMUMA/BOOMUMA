import pandas as pd
import numpy as np

def clean_and_transform_student_data(student_data):
    # 使用Numpy将'NaN'转换为NaN，并将TestScore转换为浮点数格式
    student_data['TestScore'] = pd.to_numeric(student_data['TestScore'], errors='coerce')

    # 过滤2020年1月1日之前注册的学生
    student_data = student_data[student_data['EnrollmentDate'] >= '2020-01-01']

    # 计算"TestScore"列非NaN值的平均值
    average_score = student_data['TestScore'].mean()

    # 复制DataFrame，避免警告。例如：student_data = student_data.copy()
    student_data = student_data.copy()

    # 使用平均分填充NaN值，例如：fillna(int(average_score), inplace=True)
    student_data['TestScore'].fillna(int(average_score), inplace=True)

    # 返回结果
    return student_data

def convert_input_to_df(input_line):
    data = [item.split() for item in input_line[1:]]
    return pd.DataFrame(data, columns=['Name', 'EnrollmentDate', 'TestScore'])

# 样本输入
_input_list = "6,Alice 2019-07-15 90,Bob 2020-02-20 NaN,Charlie 2019-11-30 85,David 2021-04-10 NaN,Eve 2020-05-25 75,Francis 2022-09-18 80".split(",")
# 将输入转换为DataFrame
df = convert_input_to_df(_input_list)
# 清理和转换数据
cleaned_df = clean_and_transform_student_data(df)
# 将DataFrame转换为字符串格式
cleaned_df_str = cleaned_df.to_string(index=False)

print(cleaned_df_str)- 👋 Hi, I’m @BOOMUMA
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
BOOMUMA/BOOMUMA is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
