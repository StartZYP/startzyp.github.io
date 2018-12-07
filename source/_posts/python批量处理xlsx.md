---
title: python批量处理xlsx
date: 2018-10-16 21:24:44
tags: python
categories: python
---

## 批量处理xlsx

针对excel读取操作

使用python的openpyxl模块中的load_workbook

加载xlsx文件

```python
wb = load_workbook(filename=file_name)
```

选择页

```python
sheet_ranges = wb['Sheet1']
```

取出B1单元的值

```python
sheet_ranges['B1'].value
```

修改Xlsx，同样选择页面

```python
ws = wb['Sheet1']
```

修改表格单元

```python
ws["I2"] ="这是修改内容"
```

最后记住保存

```python
wb.save(file_name)
```