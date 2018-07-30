---
layout: post
title: My First Blog Post ! 
---

```python
import pandas as pd
import numpy as np 
from matplotlib import pyplot as plt
import seaborn as sns
%pylab inline
```

    Populating the interactive namespace from numpy and matplotlib



```python
inventory = pd.read_csv("WeeklyWholesaleMarketPrices_PrixHebdomadaireMarcheGros55.csv")
inventory.head(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>CentreEn_CentreAn</th>
      <th>CentreFr_CentreFr</th>
      <th>CmdtyEn_PrdtAn</th>
      <th>CmdtyEn_PrdtFr</th>
      <th>VrtyEn_VrteAn</th>
      <th>VrtyFr_VrteFr</th>
      <th>GradeEn_CtgryAn</th>
      <th>GradeFr_CtgryFr</th>
      <th>Cntry_Pays</th>
      <th>...</th>
      <th>PkgTypeEn_EmpqtgAn</th>
      <th>PkgTypeFr_EmpqtgFr</th>
      <th>CntrTypeEn_TypeCntrAn</th>
      <th>CntrTypeFr_TypeCntrFr</th>
      <th>PkgQty_QtePqt</th>
      <th>PkgWt_PdsPqt</th>
      <th>UnitMsrEn_QteUnitAn</th>
      <th>UnitMsrFr_QteUnitFr</th>
      <th>PkgSizeEn_TaillePqtAn</th>
      <th>PkgSizeFr_TaillePqtFr</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2017-07-07</td>
      <td>Wholesale-Calgary</td>
      <td>Prix de gros-Calgary</td>
      <td>ALFALFA SPROUTS</td>
      <td>GERMES DE LUZERNE</td>
      <td>UNSPECIFIED</td>
      <td>INCONNUE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>CA</td>
      <td>...</td>
      <td>Ctn 12X130 Gr</td>
      <td>Ctn 12X130 Gr</td>
      <td>Ctn</td>
      <td>Ctn</td>
      <td>12.0</td>
      <td>130.0</td>
      <td>Gr</td>
      <td>Gr</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2017-07-07</td>
      <td>Wholesale-Edmonton</td>
      <td>Prix de gros-Edmonton</td>
      <td>ALFALFA SPROUTS</td>
      <td>GERMES DE LUZERNE</td>
      <td>UNSPECIFIED</td>
      <td>INCONNUE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>CA</td>
      <td>...</td>
      <td>Ctn 12X130 Gr</td>
      <td>Ctn 12X130 Gr</td>
      <td>Ctn</td>
      <td>Ctn</td>
      <td>12.0</td>
      <td>130.0</td>
      <td>Gr</td>
      <td>Gr</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2017-07-07</td>
      <td>Wholesale-Regina</td>
      <td>Prix de gros-Regina</td>
      <td>ALFALFA SPROUTS</td>
      <td>GERMES DE LUZERNE</td>
      <td>UNSPECIFIED</td>
      <td>INCONNUE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>MX</td>
      <td>...</td>
      <td>Ctn 12X120 Gr</td>
      <td>Ctn 12X120 Gr</td>
      <td>Ctn</td>
      <td>Ctn</td>
      <td>12.0</td>
      <td>120.0</td>
      <td>Gr</td>
      <td>Gr</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>3 rows × 23 columns</p>
</div>




```python
counts = inventory.groupby(['CmdtyEn_PrdtAn'])['Date'].count()
sorted_counts = counts.sort_values()
rare_fruit_shipments = sorted_counts[0:8]
final_table = rare_fruit_shipments.to_frame().reset_index()
final_table.columns = ['Item','Count']
final_table
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Item</th>
      <th>Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>BROCOFLOWER</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>FIDDLEHEADS</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>CURRANTS GOOSEBERRY</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>TAMARILLO</td>
      <td>4</td>
    </tr>
    <tr>
      <th>4</th>
      <td>LYCHEE</td>
      <td>5</td>
    </tr>
    <tr>
      <th>5</th>
      <td>CARAMBOLA</td>
      <td>13</td>
    </tr>
    <tr>
      <th>6</th>
      <td>SUGAR CANE</td>
      <td>29</td>
    </tr>
    <tr>
      <th>7</th>
      <td>PLUOTS</td>
      <td>30</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.figure(figsize=(10, 10))
plt.pie(final_table['Count'],labels =final_table['Item'],autopct='%1.1f%%',shadow=True)
plt.show();
```


![_config.yml]({{ site.baseurl }}/images/rare_fruits_3_0.png)




