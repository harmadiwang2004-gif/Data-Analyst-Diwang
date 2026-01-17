#Data Analyst
## Facies Data
from google.colab import files

uploaded = files.upload()

for fn in uploaded.keys():
  print('User uploaded file "{name}" with length {length} bytes'.format(
      name=fn, length=len(uploaded[fn])))
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
     

data = pd.read_csv('facies_data2.csv')
data.head()
