![image](https://github.com/user-attachments/assets/09a0f497-548b-4b37-b8a5-544c791a5dde)# Embedding

## Supabase Prep:
1. build a project
2. make a table ```documents```, cheklist the ```Enable Row Level Security``` and set with a column :
```
id : int8; -> primary key
content : text;
metadata : jsonb;
type : text;
chunk_id : uuid
```
3. disable the RLS (Row Level Security) by clicking ```Add RLS policy -> 
Disable RLS -> Confirm```
4. make a table ```tables```, cheklist the ```Enable Row Level Security``` and set with a column :
```
chunk_id : uuid -> primary key
table_data : jsonb;
metadata : jsonb;
description : text
```
5. disable the RLS (Row Level Security) by clicking ```Add RLS policy -> 
Disable RLS -> Confirm```

# Obtain DB_CONNECTION for embedding storage 
1. go to "Connect" option in the top bar of your project page
![image](https://github.com/user-attachments/assets/4b5bf5ba-b276-4f3a-9248-9ca7df3bee33)
2. copy the connection string URI

# Run code in local:
1. install the ```requirements.txt``` first in your environment
2. fill the ```.env``` supabase url and the API key
3. make sure the input and output folder in the same folder as code and other dependencies
4. If the venv supports GPU, make sure install the PyTorch with the correct CUDA version. (my system supports CUDA 12.5, so i run this ```pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121```)
5. if find some error while loading the model, make sure to test your env supported GPU or not, by running the ```test.py``` first. Expected result :
   ```
   "CUDA Available: True"
   "GPU Name: NVIDIA GeForce RTX 3050".
   ```
   if you have GPU but its not detected, run ```nvidia-smi``` in the cmd first
7. the code also can be run in the CPU

![4_embedding_supabase](https://github.com/user-attachments/assets/d5ec6f04-6f01-4b80-8e4e-682a9718eed6)


## API running
1. run by the API by activate the venv first, then ```python api.py```
2. i made another file in ```api.py``` for integrating with fastapi without changing the ```main.py```
3. don't forget to open http url in browser and add the ```{url}/docs``` to run the function method available

![4_embedding_completed](https://github.com/user-attachments/assets/b634d070-73f4-4a3d-98f9-0ce62f2ff302)


