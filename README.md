# Retail_Sales_Dataset_Project

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

a = pd.read_csv("C:/Users/Sonu/OneDrive/Desktop/retail_sales_dataset.csv")

#Creating dataframe
df = pd.DataFrame(a)
#print(df)

#print(a.info())
#a.describe()

#print(a.isnull().sum())

#print(a["Customer ID"].duplicated().sum())
#print(a.drop_duplicates("Customer ID"))





gb = df.groupby("Product Category").agg({"Total Amount":"sum"})
#print(gb)

# visualising
plt.bar(gb.index, gb["Total Amount"])
plt.title("Sales Based On Product Category")
plt.xticks(rotation = 90)
plt.xlabel("Product Category")
plt.ylabel("Total Sales Amount")
plt.show()


gb1 = df.groupby("Gender").agg({"Total Amount":"sum"})
# print(gb1)

plt.bar(gb1.index, gb1["Total Amount"])
plt.title("Sales Based On Gender")
plt.xticks(rotation = 90)
plt.xlabel("Product Category")
plt.ylabel("Total Sales Amount")
plt.show()


plt.violinplot(df["Age"], showmedians = True)
plt.title("Customer Segmentation Based On Age")
plt.ylabel("Customer Age")
plt.show()


plt.violinplot(df["Total Amount"], showmedians = True)
plt.title("Usual Purchase Amount") 
plt.ylabel("Purchase Amount")
plt.show()


# Create a violin plot with Seaborn
sns.violinplot(y="Price per Unit", data=df)
plt.title("Product Pricing That People Usually Buy")
plt.ylabel("Price Per Unit")
plt.show()
