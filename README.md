---
jupyter:
  colab:
  kernelspec:
    display_name: Python 3
    name: python3
  language_info:
    name: python
  nbformat: 4
  nbformat_minor: 0
---

<div class="cell markdown" id="cEe3nSvoWhpf">

## **College student salary background**

### **Description**：

Dataset describing the starting median salary of different college
student in U.S.

**Github:**
<https://github.com/prasertcbs/basic-dataset/blob/master/college-salaries/salaries-by-region.csv>

**Sample size**: 179

</div>

<div class="cell markdown" id="POimjMFCa83r">

## Hypothesis

-   Tell us what your idea is and why you have chosen to pursue this
    idea.
    -   We are interested in "*Southern student or Northeastern student
        have a higher average starting median salary?*"
-   What two groups you are comparing:
    -   **G1**: Student in Southern; **G2**: Student in Northeastern
-   What you will be measuring (i.e., what your response variable will
    be)
    -   `Starting Median Salary`
-   Is your response variable quantitative rather than categorical?
    -   `Starting Median Salary` is continuous data, which can be
        regarded as a quantitative variable.
-   Make a prediction about what kind of difference you expect to see
    between your samples and WHY.
    -   We'd expect that **G2** \> **G1**
    -   Reason: Northeastern have a higher cost of living
-   Talk about how you will gather your data
    -   From Github link:
        <https://github.com/prasertcbs/basic-dataset/blob/master/college-salaries/salaries-by-region.csv>
-   If you had unlimited resources (time, money, staff, etc.) how would
    you collect your data?
    -   \(i\) Attempt to collect more data on each college to find a
        more precise starting median salary for calculating the average
        ; (ii)Attempt to collect more details such as subject type,
        company, cgpa etc.

</div>

<div class="cell markdown" id="XDetuIlTQB8u">

## Prepare your dataset

</div>

<div class="cell code" execution_count="5"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:302}"
id="RrNSmw_vQMXY" outputId="01c524c4-07f2-4a2a-9f48-df8120361c10">

``` python
## load dataset from github

import pandas as pd

df = pd.read_csv('https://raw.githubusercontent.com/prasertcbs/basic-dataset/master/college-salaries/salaries-by-region.csv')
df.head(5)
```

<div class="output execute_result" execution_count="5">

                                    School Name      Region  \
    0                       Stanford University  California   
    1  California Institute of Technology (CIT)  California   
    2                       Harvey Mudd College  California   
    3        University of California, Berkeley  California   
    4                        Occidental College  California   

      Starting Median Salary Mid-Career Median Salary  \
    0             $70,400.00              $129,000.00   
    1             $75,500.00              $123,000.00   
    2             $71,800.00              $122,000.00   
    3             $59,900.00              $112,000.00   
    4             $51,900.00              $105,000.00   

      Mid-Career 10th Percentile Salary Mid-Career 25th Percentile Salary  \
    0                        $68,400.00                        $93,100.00   
    1                               NaN                       $104,000.00   
    2                               NaN                        $96,000.00   
    3                        $59,500.00                        $81,000.00   
    4                               NaN                        $54,800.00   

      Mid-Career 75th Percentile Salary Mid-Career 90th Percentile Salary  
    0                       $184,000.00                       $257,000.00  
    1                       $161,000.00                               NaN  
    2                       $180,000.00                               NaN  
    3                       $149,000.00                       $201,000.00  
    4                       $157,000.00                               NaN  

</div>

</div>

<div class="cell markdown" id="z3F1ccscRWeQ">

-   Tell us what groups you want to compare in the dataset
    -   **G1** (Starting Median Salary \| Region = Southern) vs. **G2**
        (Starting Median Salary \| Region = Northeastern)

</div>

<div class="cell markdown" id="1scwxrlBR8aX">

-   Print first 5 records of each group, respectively.

</div>

<div class="cell code" execution_count="6"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="BRH8iYhkR-zj" outputId="b3463c86-563f-4b96-fb35-f05b33e05833">

``` python
## First 5 records of G1(Southern)
(df[df['Region']=='Southern']['Starting Median Salary']).head(5)
```

<div class="output execute_result" execution_count="6">

    141    $64,000.00
    142    $55,000.00
    143    $58,900.00
    144    $58,300.00
    145    $53,600.00
    Name: Starting Median Salary, dtype: object

</div>

</div>

<div class="cell code" execution_count="7"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="_xLYyQyjS8z0" outputId="c421fcad-1b8b-40cb-d51e-88bdebeeb84a">

``` python
## First 5 records of G2(Northeastern)
(df[df['Region']=='Northeastern']['Starting Median Salary']).head(5)
```

<div class="output execute_result" execution_count="7">

    220    $58,000.00
    221    $66,500.00
    222    $72,200.00
    223    $59,100.00
    224    $63,400.00
    Name: Starting Median Salary, dtype: object

</div>

</div>

<div class="cell code" id="BClMQUKGT6_c">

``` python
## Any other data description and visualization you want to add.
```

</div>

<div class="cell markdown" id="QIKgyrPzUAv8">

-   Measure of central tendency

</div>

<div class="cell code" execution_count="22"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:219}"
id="HYUir5SbUp1g" outputId="748d2074-470e-4614-bf5d-d90b33b1e300">

``` python
## Mean of G1(Southern)
str.replace('$','')

print(df[df['Region'] == 'Southern']['Starting Median Salary'].mean())
```

<div class="output error" ename="TypeError" evalue="ignored">

    ---------------------------------------------------------------------------
    TypeError                                 Traceback (most recent call last)
    <ipython-input-22-ef2d3a2f90e9> in <module>
          1 ## Mean of G1(Southern)
    ----> 2 str.replace('$','')
          3 
          4 print(df[df['Region'] == 'Southern']['Starting Median Salary'].mean())

    TypeError: replace expected at least 2 arguments, got 1

</div>

</div>

<div class="cell code" execution_count="23"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:219}"
id="Cynv_V2nZ71o" outputId="8203461a-46d6-4c74-a70f-db8d13d093c4">

``` python
## Mean of G2(Northeastern)
str.replace('$','')

print(df[df['Region'] == 'Northeastern']['Starting Median Salary'].mean())
```

<div class="output error" ename="TypeError" evalue="ignored">

    ---------------------------------------------------------------------------
    TypeError                                 Traceback (most recent call last)
    <ipython-input-23-250c343daf5f> in <module>
          1 ## Mean of G2(Northeastern)
    ----> 2 str.replace('$','')
          3 
          4 print(df[df['Region'] == 'Northeastern']['Starting Median Salary'].mean())

    TypeError: replace expected at least 2 arguments, got 1

</div>

</div>

<div class="cell code" execution_count="28"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="_1ehR3dwaJCd" outputId="b75d8b3f-cedf-417d-a221-67155e7033e9">

``` python
## Maximum and minimum value in G1(Southern)
df[df['Region'] == 'Southern']['Starting Median Salary'].agg(['min','max'])
```

<div class="output execute_result" execution_count="28">

    min    $34,500.00
    max    $64,000.00
    Name: Starting Median Salary, dtype: object

</div>

</div>

<div class="cell code" execution_count="29"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="JfkFgwA-bSks" outputId="10501ab3-32e8-44f9-98c1-b72a06bc8989">

``` python
## Maximum and minimum value in G2(Northeastern)
df[df['Region'] == 'Northeastern']['Starting Median Salary'].agg(['min','max'])
```

<div class="output execute_result" execution_count="29">

    min    $36,900.00
    max    $72,200.00
    Name: Starting Median Salary, dtype: object

</div>

</div>

<div class="cell code" execution_count="35" id="HJFMr1tvdpSp">

``` python
import matplotlib.pyplot as plt
import seaborn as sns
plt.rcParams['figure.figsize'] = [10, 5]

sns.set()
```

</div>

<div class="cell markdown" id="RnM8V9sJgFYn">

-   Data visualization

</div>

<div class="cell code" execution_count="43"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:339}"
id="U9zTKK5Zdqki" outputId="e606d241-9801-4568-effe-141eae49c555">

``` python
## Stripplot of G1(Southern)
sns.stripplot(data=df[df['Region']=='Southern'], x='Starting Median Salary')
plt.show()
```

<div class="output display_data">

![](cc1c87c7950dad3b730ff8286a204dc50ab7a101.png)

</div>

</div>

<div class="cell code" execution_count="44"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:339}"
id="1_Gd55VXf4Td" outputId="20e6682d-d539-40fd-e73d-6ba22dd29095">

``` python
## Stripplot of G2(Northeastern)
sns.stripplot(data=df[df['Region']=='Northeastern'], x='Starting Median Salary')
plt.show()
```

<div class="output display_data">

![](551886fa513bbe596a8a08aeab24fa6667fe9925.png)

</div>

</div>
