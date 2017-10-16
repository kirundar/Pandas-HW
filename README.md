#Dependencies
import pandas as pd
import numpy as np
import json
import os
#import data
json_path = 'C:\\Users\\kirun\\desktop\\GW_clone\\09-12-2017-GW-Arlington-Class-Repository-DATA\\Homework\\Week04\\Instructions\\HeroesOfPymoli\\purchase_data.json'
p_data_df = pd.read_json(json_path)
p_data_df.head()
#Total number of players
player_count=p_data_df['SN'].count()
p_data_df['SN'].count()
#Purchasing Analysis (Total)
#Number of Unique items
unique_items= len(p_data_df["Item Name"].unique())
unique_items
#Average Purchase price
avg_purchase=p_data_df['Price'].mean()
avg_purchase
#Total# of Purchases
total_purchases=p_data_df['Item Name'].count()
total_purchases
#Total Revenue
total_revenue=p_data_df['Price'].sum()
total_revenue
#Gender Demographics
#Count of Male players
male=p_data_df['Gender'].value_counts()['Male']
male
#percentage of Male players
male_percentage=(male/player_count)*100
male_percentage
#Gender Demographics
#Count of Female players
Female=p_data_df['Gender'].value_counts()['Female']
Female
#percentage of Female players
Female_percentage=(Female/player_count)*100
Female_percentage
#Gender Demographics
#Count of Other/Non-disclosed players
Non_disclosed=p_data_df['Gender'].value_counts()
Non_disclosed
Ither_ND= player_count- male-Female
Ither_ND
Ither_ND_Percentage=(Ither_ND/player_count)*100
Ither_ND_Percentage
#purchasing Analysis
#by Gender
#Male
male_df=p_data_df.loc[p_data_df["Gender"]=="Male"]
male_df.head()
male_pc=male_df["Item Name"].count()
print(f"male_pc:{male_pc}")
avg_pur_count_male=male_df["Price"].mean()
print(f"avg_pur_count_male:{avg_pur_count_male}")
total_Pur_value=male_df["Price"].sum()
print(f"total_Pur_value:{total_Pur_value}")
male_NP= np.std(avg_pur_count_male)
print(f"male_NP:{male_NP}")
# Create bins of 4 years (i.e.<10, 10-14, 15-19 etc.)
bin_value = [0, 9, 14, 19, 24, 29, 34, 39, 44, 100]
# Create the names for the four bins
bin_names = ['<10', '10-14', '15-19','20-24','25-29', '30-34','35-39','40-44','45']
p_data_df["Age Demographics"]=pd.cut(p_data_df["Age"],age_bin_value, labels=bin_names)
p_data_df
demographic_group = p_data_df.groupby("Age Demographics")
print(demographic_group["Item Name"].count())
print(demographic_group["Price"].mean())
print(demographic_group["Price"].sum())
