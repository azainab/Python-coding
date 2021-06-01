# Python-coding

# output the list of drawdowns as per the concept of finance

import pandas as pd

import numpy as np

d = {'Returns': [3,2,4,5,3,2,4,6,3,4,2,5]}

df = pd.DataFrame(data=d)


Roll_Max = df['Returns'].cummax()

Daily_Drawdown = df['Returns']/Roll_Max - 1.0

Max_Daily_Drawdown = Daily_Drawdown.cummin()

list1 = {}

for i in range(0, len(Daily_Drawdown)-1):

    list1[i] = Daily_Drawdown[i]<Daily_Drawdown[i+1]

ans = []

for i in list1:

    print(list1[i])
    
    if list1[i] == True:
    
        print("i", i)
        
        ans.append(np.abs(Max_Daily_Drawdown[i]))
        
        print("ans", ans)
        
    else:
    
        continue

result = np.sort(np.unique(ans))

print(result)

