# Retrieving Wikipedia Articles

Main tasks

1. Load and transform real, text data
2. Compare results with word counts and TF-IDF
3. Set the distance function in the reterival
4. Build a document retrieval model using nearest neighbor search 

#### **Resources you will need**

- Make sure you have downloaded and installed Python, iPython notebook and GraphLab Create. [You can find the instructions here](https://eventing.coursera.org/api/redirectStrict/GcisOGuMlUuHxHnOJT7Uymj1xy3E8lJCtbVsp7z3DS3HqQI-6363aiXO6oeYIs9b-JCx-3mALcZWNjA4JIcksw.A0uAR3GuoQXmeVALBrDI0A.iqzUGJhqNzlEvqOO8s1vLtGxYslF6DmqYp62noMaIYRTSV0zLD-mjDDCzYMhzwWW6-kiCDx0Fef02_5e910dOlk7v4TO_aWCuhXgrenCHlhzeypL-MbAG83z5ohXjcLVCTUDfe8i4Q_c6X7-Ma74kmyNZK4u1yrTosmuzkQ-el0xlsUc4OFU4g-QD9BLSp0NgfTuTUAWXnePSiFCfKOO8XMudrxYVjNgJFdFDVQ9dZwTFu1Rsr4ilxx3BdkCJ8K0e9NbkTaC61-aZE2Bmns-0csynm2-0JAZvQAgzvjfJmU). _(If you are using an ML package other than GraphLab Create, please see the note below.)_
- There are many Python resources available online. [Here is a good place for documentation](https://eventing.coursera.org/api/redirectStrict/Pd5dN7A7A5xEby8hM1ldx6mxIIjqWk4JT_7KMZ1lit-kURdEc7GHPlhRKkEqNMqpuSOUpce9FjIpfocZsja9lg.T46On5GxTO5h5Jx_NWaZjQ.ywuDqNw_xZhQQF4qB9MzDkcPnqgDxFFVTEy51GyXZwr7nX6uw1RXKfEWzOpVKBPhAHHbIz08hFNfiKndMSOGTxdxfojwTkwKt04L6JFj7NArtobdTt8KVHaqcml9xvW8y4__Sepjvl5_L72TXNqnO5nc77f1Ge23VLC94wO89sgKCoFv4MDCyRvBrmlztsl8aXSrEqRYCNX5rkIjEw54axaJ_2hHJlVfewsYu4dhJrIUFlWYImb87qayVNXuVL7UgQqqDHdMIRR0kEeWJlNHRSgP_lvLUIAe3BrgMq0PkVNQTllTno13gsFD4f_HGt0W).
- For GraphLab Create, there is also a lot of information available online. Here are some starting points.

 Learning Concepts about the Tools [https://dato.com/learn/](https://eventing.coursera.org/api/redirectStrict/Lt6aM37Npqa5kZ1QwPExd8IyJ8A0wLXoACmKUeZIvn61Sg8iWD-tMgppXKvXjIADNDxqclenEdyKuFyuLNOcfg._LePR5kVsB9AqVPzrQCfRg.LlgkSPjt4cZH-A8HwjncQU0VAQg6ISmu7IO21Iv1vYY497xdvoDPPuDB0gvx4bVV5jIM8sOpJyti9M3B_TXUc9nkvq2t3pxSI5ygTxcUULm4R-p5ONWnQs3WBzQRzdJb1xovTDDJ9xgtovD1GeLSKmeO_XI0K3bBLqbK_GtN0FBOq0qTPLPFC1NfkNZDbM4DpAyl2vPJJ3VHEbuKUodJfKAi6LTp70_milZXtsOgIhF2QcipLBB18kDci4tROpLeqARD_AqzWDhYu6fvmW7WrA)

 The User Guide [https://dato.com/learn/userguide/](https://eventing.coursera.org/api/redirectStrict/zN1clf0M6ZfZ1hbt_Q2m8j4Ihh74uxTkSdr6HU2_ag1fFgzH8Hj77cl4GpJVBjUOxT6Ujkgf-zMIk9ev5KuPpQ.FkmF96CiubDCVenLBOMUfw.VMevDO8vKjfMngqCHAzCPtfI6_k5xzNG4YUzPZEloUZLUxPaxsuemf73trVGuxFU_aCIRQdyWa6C38hCvu1Py5r4dx-WAkGPyoop4TraIZp5aHx_CEEwVz_0rwohuNOzoAgW4kRxc2LQ8eqGFzU8F1G51aPenKy7JDDlRwiqgfZ2nIB2lr3o-cYbb5lvp5u0RUjS5pCwv9d5fnAN1d7OxZpzvGx7C4wYp9cp3YqtWV89_2tccgk_aHWxMIa5skYpnyLiQcqtmPfbTqG4_P7SEB_j09cU1sZ3TJJRt96cBZw)

 More Detailed API Docs [https://dato.com/products/create/docs/](https://eventing.coursera.org/api/redirectStrict/n2D9XSHMw2EDEAEV2qKCXWGNftFvlqSO1A2LXv2-dRpLqW8liaeMWf945P_MVdWYbeitXT03zYN7DP2jNH8KpQ.7qet8d-VvOGF4BPhg4Ccyw.21DbBvper_jwbH5qkU6oOk6PCwUsxmXDTXma3KLD9IYsNztJd4bWmP6D13ZVpRV_w8i5HZ4gwQni6XNaj_BgDmz-26wKfO0Uh2Nbk065lv38EF1cQlcYsFbLK6zb4pCey-_Lhvq0e034xclUwE9b6AgkRqktvBYjZP2Zw9dp4FINzNu211102Yzg_qa-f0TgEXWbUq58eqWz1UYhPf_p4-57sk5DPiDUbzS08Tryypf-K1dRxuuh8A-BOcbgOJD5YYOP8PQd0PgepPcByuVDUnv0doIhsCvAbu1QQSM6b1s71-L7Ym1kTbFnG2I0-Ogk)

#### Download the data and starter code

Before getting started, you will need to download the dataset and the starter iPython notebook that we used in the module.

- Download the wikipedia dataset with articles on famous people here in SFrame format: **[people_wiki.gl.zip](https://eventing.coursera.org/api/redirectStrict/GKsSRrYkoeGfc5XjAKr6ncJ3J2ubnIm999yQqv35HDem2Ta9G7KHR0vHwNYFo0f-Z6Vmdknu3Zu3bUKLjLaN0g.dQ7WrvOu097_hXA-L_GwEQ.jyciXHStsYv3slLocnd8PMgNlMfQWxmgbAG7CjqHwZynJhmlBupunsBPgk-m9M5gtckqHwtnp2xIuaeanrjL3wCNfhycxlTM4wSZ4paOra3d-e2T9AYkf1jHWbcm07PeSsoRpDGFCc2sMLE12rGGiGh8lb5VTCsXWLhrOlxJI-y2A5xRb_TfJIyNsYFZLqGohOxhZfZ4cTuQUcWVYNkUyfXoza0Sfy4Oh8uN56yKkyggBgWBvh75PKH_OQQBYQr_hq-Ktl_KHyfJWYhLZTos9J1vI0ZWyc2SMih3Giemggw7un5IsVJfzQKXQGc_LHRuCFcTj9qx87eY_v1dD-j9ZFmuDwJH7hqnkPdGKFJ5dLWH8yqlATycr-Hg6VneVoy_07fpLFLomtWuNxpJLjTsTmWev8hmLtwzDUIyY55Ik1TJkty7b4xuj4smVD7pWEE9)**
- Download the document retrieval notebook from the module here: **[Document retrieval.ipynb](https://eventing.coursera.org/api/redirectStrict/_eqO9XZ27B170KFo6clxBJ4oi_yUvcMdqdekzCHFeafU_qeMrfxrQ60VWa0qrt-n4mfHhY2fzLK2sgG9Za7ynA.YZZBch-KNR48GrGoeaY5Kg.FiFl2enCXjdviicIHf89_Hzi99nT8sWn8DbvAf5onC4LPyTKlB8PpUYW-gLgT8JYHe9PeULpoA_OcjOEX14E3Y9ojALKbUIQ2D1_816EstaQn-ceebdzxnpqGo6Is07Hskmf-YpQTMhG4miRnyOH9e-6Fev842APTR7ruYgihl0S1PYvS2wDYKo8sxxGWGsVtTsVrS20O4ChC6L_-evQKu9pcWT0QeP6nLzQpaC7I41_UGgy_5pjbxaXu2ePbeooQ_R4chYpR65iDGp-nbY9tYwU_4KubldVY8C9rhqXU6n91OG4wjRzTxG9ViuFTmGtto2Z-d5VPGLww-yhJf0b0U94KEiKBEPqUBYRpRujfrmivgJWZwM-E2dvZ88V7H8mIaop5xwB46vN189WWiyhGncNgZyR29izgBa_fQlsQjnXT6qoAlDZEq8L_S6EvTcB28A6fNoFHHRKnBus5r5yuw)**
- Save both of these files in the same directory (where you are calling iPython notebook from) and unzip the data file.


# Results

Nearest neighbors method is used. When using 'word_count' and 'tfidf' as features, the model results are different.

Number of reviews based on products

![alt text](https://github.com/EvanWang2015/Data_Science/blob/master/Document_Retreval_TF_IDF/images/training_model.PNG "Document Retrieval")

Closest neighbor of 'Elton John' while using raw word counts.

![alt text](https://github.com/EvanWang2015/Data_Science/blob/master/Document_Retreval_TF_IDF/images/elton.PNG "Document Retrieval")

Closest neighbor of 'Elton John' using TF-IDF vectors.

![alt text](https://github.com/EvanWang2015/Data_Science/blob/master/Document_Retreval_TF_IDF/images/elton_tfidf.PNG "Document Retrieval")
