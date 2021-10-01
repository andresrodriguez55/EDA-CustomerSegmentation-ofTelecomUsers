# Information

| Column Name| Description |
| --- | --- |
| customerID | customer id |
| gender | client gender (male / female) |
| SeniorCitizen | is the client retired (1, 0) |
| Partner | is the client married (Yes, No) |
| tenure | how many months a person has been a client of the company |
| PhoneService | is the telephone service connected (Yes, No) |
| MultipleLines | are multiple phone lines connected (Yes, No, No phone service) |
| InternetService | client's Internet service provider (DSL, Fiber optic, No) |
| OnlineSecurity | is the online security service connected (Yes, No, No internet service) |
| OnlineBackup | is the online backup service activated (Yes, No, No internet service) |
| DeviceProtection | does the client have equipment insurance (Yes, No, No internet service) |
| TechSupport | is the technical support service connected (Yes, No, No internet service) |
| StreamingTV | is the streaming TV service connected (Yes, No, No internet service) |
| StreamingMovies | is the streaming cinema service activated (Yes, No, No internet service) |
| Contract | type of customer contract (Month-to-month, One year, Two year) |
| PaperlessBilling | whether the client uses paperless billing (Yes, No) |
| PaymentMethod | payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic)) |
| MonthlyCharges | current monthly payment |
| TotalCharges | the total amount that the client paid for the services for the entire time |
| Churn | whether there was a churn (Yes or No) |

Churn is the measure of how many customers stop using a product. This can be measured based on actual usage or failure to renew (when the product is sold using a subscription model).


```python
import pandas as pd

df=pd.read_csv("telecom_users.csv")
df
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
      <th>Unnamed: 0</th>
      <th>customerID</th>
      <th>gender</th>
      <th>SeniorCitizen</th>
      <th>Partner</th>
      <th>Dependents</th>
      <th>tenure</th>
      <th>PhoneService</th>
      <th>MultipleLines</th>
      <th>InternetService</th>
      <th>...</th>
      <th>DeviceProtection</th>
      <th>TechSupport</th>
      <th>StreamingTV</th>
      <th>StreamingMovies</th>
      <th>Contract</th>
      <th>PaperlessBilling</th>
      <th>PaymentMethod</th>
      <th>MonthlyCharges</th>
      <th>TotalCharges</th>
      <th>Churn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1869</td>
      <td>7010-BRBUU</td>
      <td>Male</td>
      <td>0</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>72</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>...</td>
      <td>No internet service</td>
      <td>No internet service</td>
      <td>No internet service</td>
      <td>No internet service</td>
      <td>Two year</td>
      <td>No</td>
      <td>Credit card (automatic)</td>
      <td>24.10</td>
      <td>1734.65</td>
      <td>No</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4528</td>
      <td>9688-YGXVR</td>
      <td>Female</td>
      <td>0</td>
      <td>No</td>
      <td>No</td>
      <td>44</td>
      <td>Yes</td>
      <td>No</td>
      <td>Fiber optic</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>Yes</td>
      <td>No</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Credit card (automatic)</td>
      <td>88.15</td>
      <td>3973.2</td>
      <td>No</td>
    </tr>
    <tr>
      <th>2</th>
      <td>6344</td>
      <td>9286-DOJGF</td>
      <td>Female</td>
      <td>1</td>
      <td>Yes</td>
      <td>No</td>
      <td>38</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Fiber optic</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Bank transfer (automatic)</td>
      <td>74.95</td>
      <td>2869.85</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>3</th>
      <td>6739</td>
      <td>6994-KERXL</td>
      <td>Male</td>
      <td>0</td>
      <td>No</td>
      <td>No</td>
      <td>4</td>
      <td>Yes</td>
      <td>No</td>
      <td>DSL</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Electronic check</td>
      <td>55.90</td>
      <td>238.5</td>
      <td>No</td>
    </tr>
    <tr>
      <th>4</th>
      <td>432</td>
      <td>2181-UAESM</td>
      <td>Male</td>
      <td>0</td>
      <td>No</td>
      <td>No</td>
      <td>2</td>
      <td>Yes</td>
      <td>No</td>
      <td>DSL</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Month-to-month</td>
      <td>No</td>
      <td>Electronic check</td>
      <td>53.45</td>
      <td>119.5</td>
      <td>No</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>5981</th>
      <td>3772</td>
      <td>0684-AOSIH</td>
      <td>Male</td>
      <td>0</td>
      <td>Yes</td>
      <td>No</td>
      <td>1</td>
      <td>Yes</td>
      <td>No</td>
      <td>Fiber optic</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Electronic check</td>
      <td>95.00</td>
      <td>95</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>5982</th>
      <td>5191</td>
      <td>5982-PSMKW</td>
      <td>Female</td>
      <td>0</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>23</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>DSL</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Two year</td>
      <td>Yes</td>
      <td>Credit card (automatic)</td>
      <td>91.10</td>
      <td>2198.3</td>
      <td>No</td>
    </tr>
    <tr>
      <th>5983</th>
      <td>5226</td>
      <td>8044-BGWPI</td>
      <td>Male</td>
      <td>0</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>12</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>...</td>
      <td>No internet service</td>
      <td>No internet service</td>
      <td>No internet service</td>
      <td>No internet service</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Electronic check</td>
      <td>21.15</td>
      <td>306.05</td>
      <td>No</td>
    </tr>
    <tr>
      <th>5984</th>
      <td>5390</td>
      <td>7450-NWRTR</td>
      <td>Male</td>
      <td>1</td>
      <td>No</td>
      <td>No</td>
      <td>12</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Fiber optic</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Electronic check</td>
      <td>99.45</td>
      <td>1200.15</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>5985</th>
      <td>860</td>
      <td>4795-UXVCJ</td>
      <td>Male</td>
      <td>0</td>
      <td>No</td>
      <td>No</td>
      <td>26</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>...</td>
      <td>No internet service</td>
      <td>No internet service</td>
      <td>No internet service</td>
      <td>No internet service</td>
      <td>One year</td>
      <td>No</td>
      <td>Credit card (automatic)</td>
      <td>19.80</td>
      <td>457.3</td>
      <td>No</td>
    </tr>
  </tbody>
</table>
<p>5986 rows × 22 columns</p>
</div>




```python
df.select_dtypes(exclude="object")
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
      <th>Unnamed: 0</th>
      <th>SeniorCitizen</th>
      <th>tenure</th>
      <th>MonthlyCharges</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1869</td>
      <td>0</td>
      <td>72</td>
      <td>24.10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4528</td>
      <td>0</td>
      <td>44</td>
      <td>88.15</td>
    </tr>
    <tr>
      <th>2</th>
      <td>6344</td>
      <td>1</td>
      <td>38</td>
      <td>74.95</td>
    </tr>
    <tr>
      <th>3</th>
      <td>6739</td>
      <td>0</td>
      <td>4</td>
      <td>55.90</td>
    </tr>
    <tr>
      <th>4</th>
      <td>432</td>
      <td>0</td>
      <td>2</td>
      <td>53.45</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>5981</th>
      <td>3772</td>
      <td>0</td>
      <td>1</td>
      <td>95.00</td>
    </tr>
    <tr>
      <th>5982</th>
      <td>5191</td>
      <td>0</td>
      <td>23</td>
      <td>91.10</td>
    </tr>
    <tr>
      <th>5983</th>
      <td>5226</td>
      <td>0</td>
      <td>12</td>
      <td>21.15</td>
    </tr>
    <tr>
      <th>5984</th>
      <td>5390</td>
      <td>1</td>
      <td>12</td>
      <td>99.45</td>
    </tr>
    <tr>
      <th>5985</th>
      <td>860</td>
      <td>0</td>
      <td>26</td>
      <td>19.80</td>
    </tr>
  </tbody>
</table>
<p>5986 rows × 4 columns</p>
</div>




```python
df.drop(columns=["Unnamed: 0", "customerID"], inplace=True)
```

# Visualizing Distributions

All distributions will be shown except those related to payment methods, monthly payments, etc...


```python
from matplotlib import pyplot as plt
import seaborn as sns

sns.set_style("whitegrid")
sns.set_palette("pastel")

fig, ax=plt.subplots(nrows=7, ncols=2, figsize=(20, 35))
fig.tight_layout(h_pad=10, w_pad=13)

plt.sca(ax[0, 0])
plt.pie(x=df.gender.value_counts(), labels=df.gender.value_counts().index, autopct="%1.0f%%")
ax[0, 0].set_title("Distribution of Genders", fontsize=20, pad=25)

plt.sca(ax[0, 1])
sns.countplot(x=df.SeniorCitizen, hue=df.gender)
ax[0, 1].set_title("Retired Clients", fontsize=20, pad=25)
plt.xlabel("")
plt.ylabel("")
plt.xticks(ticks=[0, 1], labels=["No", "Yes"])
plt.legend(title="Gender")

plt.sca(ax[1, 0])
sns.countplot(x=df.Partner, hue=df.gender)
ax[1, 0].set_title("Civil Status of Clients", fontsize=20, pad=25)
plt.xlabel("")
plt.ylabel("")
ax[1, 0].set_xticklabels(["Married", "Single"])
plt.legend(title="Gender")

plt.sca(ax[1, 1])
sns.histplot(x=df.tenure, hue=df.gender, multiple="stack")
ax[1, 1].set_title("Months of People Who Have Been Clients of The Company", fontsize=20, pad=25)
plt.xlabel("Months")
plt.ylabel("")

services=["Phone Service", "Multiple Lines", "Internet Service", "Online Security", "Online Backup",
          "Device Protection", "Tech Support", "Streaming TV", "Streaming Movies"]
for x in range(len(services)):
    plt.sca(ax[2+(x//2), 0+(x%2)])
    ax[2+(x//2), 0+(x%2)].set_title(services[x], fontsize=20, pad=25)
    sns.countplot(x=df[services[x].replace(" ","")], hue=df.Partner)
    plt.legend(title="Civil Status of Clients", labels=["Married", "Single"])
    plt.xlabel("")
    plt.ylabel("")
    
ax[6, 1].set_visible(False)
plt.show()
```


    
![png](output_5_0.png)
    


With this visualization we can draw several conclusions, but the most important is that married people obtain more services than singles, but instead of focusing on that point, let's visualize the data of retired clients.


```python
lostCustomers=df[df.SeniorCitizen==1].drop(columns=["SeniorCitizen"]).copy()
lostCustomers=lostCustomers.drop(columns=["Dependents"]).rename(columns={"tenure":"months", "Partner": "married"})
lostCustomers
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
      <th>gender</th>
      <th>married</th>
      <th>months</th>
      <th>PhoneService</th>
      <th>MultipleLines</th>
      <th>InternetService</th>
      <th>OnlineSecurity</th>
      <th>OnlineBackup</th>
      <th>DeviceProtection</th>
      <th>TechSupport</th>
      <th>StreamingTV</th>
      <th>StreamingMovies</th>
      <th>Contract</th>
      <th>PaperlessBilling</th>
      <th>PaymentMethod</th>
      <th>MonthlyCharges</th>
      <th>TotalCharges</th>
      <th>Churn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>Female</td>
      <td>Yes</td>
      <td>38</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Fiber optic</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Bank transfer (automatic)</td>
      <td>74.95</td>
      <td>2869.85</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Male</td>
      <td>No</td>
      <td>55</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Fiber optic</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Electronic check</td>
      <td>116.50</td>
      <td>6382.55</td>
      <td>No</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Male</td>
      <td>Yes</td>
      <td>60</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Fiber optic</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Electronic check</td>
      <td>99.00</td>
      <td>6017.9</td>
      <td>No</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Female</td>
      <td>No</td>
      <td>1</td>
      <td>Yes</td>
      <td>No</td>
      <td>Fiber optic</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Electronic check</td>
      <td>69.65</td>
      <td>69.65</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Female</td>
      <td>Yes</td>
      <td>72</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Fiber optic</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Two year</td>
      <td>No</td>
      <td>Bank transfer (automatic)</td>
      <td>78.50</td>
      <td>5602.25</td>
      <td>No</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>5965</th>
      <td>Female</td>
      <td>Yes</td>
      <td>58</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Fiber optic</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Bank transfer (automatic)</td>
      <td>100.40</td>
      <td>5749.8</td>
      <td>No</td>
    </tr>
    <tr>
      <th>5968</th>
      <td>Male</td>
      <td>Yes</td>
      <td>27</td>
      <td>Yes</td>
      <td>No</td>
      <td>Fiber optic</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Electronic check</td>
      <td>70.55</td>
      <td>1943.9</td>
      <td>No</td>
    </tr>
    <tr>
      <th>5973</th>
      <td>Female</td>
      <td>Yes</td>
      <td>1</td>
      <td>Yes</td>
      <td>No</td>
      <td>Fiber optic</td>
      <td>No</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Mailed check</td>
      <td>76.40</td>
      <td>76.4</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>5977</th>
      <td>Male</td>
      <td>Yes</td>
      <td>64</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Fiber optic</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Two year</td>
      <td>No</td>
      <td>Electronic check</td>
      <td>102.10</td>
      <td>6538.45</td>
      <td>No</td>
    </tr>
    <tr>
      <th>5984</th>
      <td>Male</td>
      <td>No</td>
      <td>12</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Fiber optic</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>No</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Month-to-month</td>
      <td>Yes</td>
      <td>Electronic check</td>
      <td>99.45</td>
      <td>1200.15</td>
      <td>Yes</td>
    </tr>
  </tbody>
</table>
<p>966 rows × 18 columns</p>
</div>




```python
fig, ax=plt.subplots(ncols=2, nrows=3, figsize=(20, 20))
fig.tight_layout(w_pad=17, h_pad=10)


plt.sca(ax[0, 0])
sns.scatterplot(x=lostCustomers.months, y=lostCustomers.MonthlyCharges, hue=lostCustomers.Contract)
ax[0, 0].set_title("Monthly Charges For Months of People Who Have Been Clients of The Company", fontsize=15, pad=25)
plt.xlabel("Months")
plt.ylabel("")


plt.sca(ax[0, 1])
sns.histplot(x=lostCustomers.MonthlyCharges, kde=True)
ax[0, 1].set_title("Monthly Charges Histogram", fontsize=15, pad=25)
plt.xlabel("Monthly Charges")
plt.ylabel("")


plt.sca(ax[1, 0])
sns.kdeplot(x=lostCustomers.months, hue=lostCustomers.PhoneService.replace({"Yes":"Phone Service", "No":"No Phone Service"})
             +" - "+lostCustomers.InternetService.replace({"No":"No Internet Service"}), multiple="stack", fill=False, palette=["red", "green", "blue", "orange"])
ax[1, 0].set_title("Kernel Density Estimation of Types of Clients", fontsize=15, pad=25)
plt.xlabel("Months Being Client")


plt.sca(ax[1, 1])
sns.countplot(x=lostCustomers[lostCustomers.PhoneService=="Yes"].MultipleLines, hue=lostCustomers.married)
plt.legend(title="Civil Status", labels=["Married", "Single"])
ax[1, 1].set_xticklabels(["Connected", "Not Connected"])
ax[1, 1].set_title("Multiple Phone Lines Connected Status of Phone Service Users", fontsize=15, pad=25)
plt.ylabel("")
plt.xlabel("")


plt.sca(ax[2, 0])

internetService=lostCustomers[lostCustomers.InternetService!="No"]
internetService=internetService[["OnlineSecurity", "OnlineBackup", "DeviceProtection", "TechSupport", "StreamingTV", "StreamingMovies"]]
internetService.reset_index(drop=True, inplace=True)
adittionalPacks={x:0 for x in range(7)}

for x in range(internetService.shape[0]):
    key=internetService.iloc[x].tolist().count("Yes")
    adittionalPacks[key]=adittionalPacks.get(key, 0)+1    
    
sns.lineplot(x=adittionalPacks.keys(), y=adittionalPacks.values())
ax[2, 0].set_title("Numbers of Clients Using Additional Internet Packages", fontsize=15, pad=25)
plt.xlabel("Additional Internet Packages Count")
plt.ylabel("Clients Count")


plt.sca(ax[2, 1])
ax[2, 1].set_title("")
sns.countplot(x=lostCustomers.Contract)
ax[2, 1].set_title("Clients Count by Contrat Types", fontsize=15, pad=25)
plt.xlabel("Contrat Type")
plt.ylabel("")

plt.suptitle("Retired Clients Data Visualization", fontsize=35, y=1.077)
plt.show()
```


    
![png](output_8_0.png)
    


We can see that retired customers if they had many additional packages, could consider price reductions. Having made these visualizations about the retired clients we have not been able to obtain profiles, what if we use the data of the retired and not retired, categorizing them by the money they spend monthly first? (So we dont have to individually look at additional packages)


```python
mix_df=df[["Partner", "tenure", "PhoneService", "InternetService", "MonthlyCharges", "Contract", "Churn"]].rename(columns={"tenure":"months", "Partner": "married"}).copy()

fig, ax=plt.subplots(nrows=1, ncols=2, figsize=(25, 9))
fig.tight_layout(pad=9)
plt.suptitle("All Historical Clients", fontsize=25,)


plt.sca(ax[0])
sns.scatterplot(x=mix_df.months, y=mix_df.MonthlyCharges, hue=mix_df.Contract)
plt.ylabel("")
plt.xlabel("Months")

plt.sca(ax[1])
sns.scatterplot(x=mix_df.months, y=mix_df.MonthlyCharges, hue=
                mix_df.PhoneService.replace({"Yes":"Phone Service", "No":"No Phone Service"})
                +" - "+mix_df.InternetService.replace({"No":"No Internet Service"}))
plt.ylabel("")
plt.xlabel("Months")
plt.legend(title="Phone and Internet Services")

plt.show()
```


    
![png](output_10_0.png)
    


Wow! There has been no one who has only used fiber optic without phone service! How about we take a look at people for combinations of internet and phone services?


```python
profilesByServices={"Phone Service - No Internet Service":mix_df[(mix_df.PhoneService=="Yes") & (mix_df.InternetService=="No")],
                   "Phone Service - Fiber Optic Internet Service":mix_df[(mix_df.PhoneService=="Yes") & (mix_df.InternetService=="Fiber optic")],
                   "Phone Service - DSL Internet Service":mix_df[(mix_df.PhoneService=="Yes") & (mix_df.InternetService=="DSL")],
                   "No Phone Service - DSL Internet Service":mix_df[(mix_df.PhoneService=="No") & (mix_df.InternetService=="DSL")]}

for profile_name in profilesByServices.keys():
    fig, ax=plt.subplots(nrows=2, ncols=3, figsize=(30, 9))
    plt.suptitle(profile_name+" User Profile", fontsize=24)
    
    plt.sca(ax[0, 0])
    ax[0, 0].set_title("Civil Status", fontsize=18)
    sns.countplot(x=profilesByServices.get(profile_name, 0).married.replace({"Yes":"Married", "No":"Single"}))
    plt.ylabel("") 
    plt.xlabel("")
    
    plt.sca(ax[0, 1])
    ax[0, 1].set_title("Distribution of Months That Have Been Clients", fontsize=18)
    sns.histplot(x=profilesByServices.get(profile_name, 0).months, kde=True)
    plt.ylabel("") 
    plt.xlabel("")
    
    plt.sca(ax[0, 2])
    ax[0, 2].set_title("Monthly Spending Distribution", fontsize=18)
    sns.histplot(x=profilesByServices.get(profile_name, 0).MonthlyCharges, kde=True)
    plt.ylabel("") 
    plt.xlabel("")
    
    plt.sca(ax[1, 0])
    ax[1, 0].set_title("Type of Contract", fontsize=18)
    sns.countplot(x=profilesByServices.get(profile_name, 0).Contract)
    plt.ylabel("") 
    plt.xlabel("")
    
    plt.sca(ax[1, 1])
    ax[1, 1].set_title("Churn", fontsize=18)
    sns.countplot(x=profilesByServices.get(profile_name, 0).Churn)
    plt.ylabel("") 
    plt.xlabel("")
    
    plt.sca(ax[1, 2])
    ax[1, 2].set_title("Churn by Type of Contract", fontsize=18)
    sns.countplot(x=profilesByServices.get(profile_name, 0)[profilesByServices.get(profile_name, 0).Churn=="Yes"].Contract)
    plt.ylabel("") 
    plt.xlabel("")
    
    plt.show()
    print("\n\n")
```


    
![png](output_12_0.png)
    


    
    
    
    


    
![png](output_12_2.png)
    


    
    
    
    


    
![png](output_12_4.png)
    


    
    
    
    


    
![png](output_12_6.png)
    


    
    
    
    

As we have seen before in the distribution of customers who left the Telecom service, we see here again that the customers who have had fiber optic and telephone services have been the ones who have left the Telecom services the most. Let's dive deeper into customer cancellation rate.


```python
fig, ax=plt.subplots(nrows=2, ncols=1, figsize=(20,14))
fig.tight_layout(h_pad=12)



plt.sca(ax[0])
ax[0].set_title("Customer Cancellation Rate", fontsize=20)
sns.histplot(x=mix_df.MonthlyCharges, hue=mix_df.Churn, multiple="stack")
plt.ylabel("Count of Clients")
plt.xlabel("Monthly Charges")



plt.sca(ax[1])
ax[1].set_title("Churn Percentages", fontsize=20)

categorical_df=df.copy()
categorical_df.MonthlyCharges=pd.cut(x=categorical_df.MonthlyCharges, bins=[x for x in range(15, 121, 5)])

categorical_churn=pd.DataFrame(categorical_df.groupby("MonthlyCharges")["Churn"].value_counts(normalize=True))
categorical_churn.iloc[:: 2]
categorical_churn.iloc[1:: 2]

indices=["("+str(x)+", "+str(5+x)+"]" for x in range(15, 120, 5)]

sns.lineplot(y=categorical_churn.iloc[:: 2].Churn, x=indices, color="blue")
sns.lineplot(y=categorical_churn.iloc[1:: 2].Churn, x=indices, color="red")
plt.ylabel("Percentage of Count of Clients")
plt.xlabel("Monthly Charges Range")

plt.show()
```


    
![png](output_14_0.png)
    


Something is happening in the range 70-105! Let's see the characteristics of only those who left Telecom in that range.


```python
fig, ax=plt.subplots(ncols=2, nrows=1, figsize=(25, 7))

range_df=df[(df.MonthlyCharges>=70)&(df.MonthlyCharges<=105)&(df.Churn=="Yes")].copy()
_2ServiceUsers=range_df[(range_df.PhoneService=="Yes")&(range_df.InternetService!="No")].shape[0]

plt.sca(ax[0])
sns.barplot(x=["1 Service Users", "2 Services Users"], y=[range_df.shape[0]-_2ServiceUsers, _2ServiceUsers])
ax[0].set_title("Internet or Phone Service Users Count")

plt.sca(ax[1])
sns.kdeplot(x=range_df.tenure, hue=range_df.PhoneService.replace({"Yes":"Phone Service", "No":"No Phone Service"})
             +" - "+range_df.InternetService.replace({"No":"No Internet Service"}), multiple="stack", fill=False)
plt.xlabel("Months Being Client")

plt.show()
```


    
![png](output_16_0.png)
    

