# DeepSliced 5G
![image](https://github.com/user-attachments/assets/917feb90-8f9a-45c6-8671-27461edeb531)

The DeepSliced 5G project showcases the capabilities of network slicing in 5G networks, utilizing deep learning techniques to optimize and manage virtual network slices. This project aims to illustrate how different slices within a 5G network can dynamically adapt to varying application requirements such as bandwidth, latency, and security.

# Dataset
I've used the data from **IEEE DataPort**.
You can preprocess the data to make it filtered data which can be used to train and test our model

# How It Works
The core of the 5G DeepSlice Demo leverages a deep learning model to achieve efficient network slicing:

**1. Data Preparation:**
Data from simulated or real-world network environments is collected and preprocessed to extract features relevant to network slicing parameters.

**2. Model Architecture:**
The neural network architecture, implemented using TensorFlow/Keras, is designed to predict optimal resource allocation and slice configurations based on input data.
![model](https://github.com/user-attachments/assets/21165406-05fc-437f-a8d0-6c68695f2745)

**3. Training:**
The model is trained on historical data or simulations to learn patterns in network behavior and optimize resource utilization across different slices.

**4. Inference and Adaptation:**
During runtime, the trained model predicts optimal configurations for network slices based on real-time or simulated network conditions.
These predictions are used to dynamically allocate resources and adjust slice parameters to meet application-specific requirements.

![image](https://github.com/user-attachments/assets/caef5415-d2be-4cbd-b94c-87b75370f537) ![image](https://github.com/user-attachments/assets/5858fcab-bfba-41ab-82ba-ab0fb75d07aa)


## Data Preprocessing

- ```"filtereddata.txt"``` was created using the Sheet 2 included in the dataset or you can make a separate ```Model_Input_Outputs.xlsx``` using the dataset.
The ```Model_Input_Outputs.xlsx``` file contains columns related to different input parameters and output types for a use case analysis.
Here are the columns based on the displayed data:

1. Unnamed: 0    // here we will drop this NULL column
2. Use CaseType (Input 1)
3. LTE/5G UE Category (Input 2)
4. Technology Supported (Input 3)
5. Day (Input 4)
6. Time (Input 5)
7. QCI (Input 6)
8. Packet Loss Rate (Reliability)
9. Packet Delay Budget (Latency)
10. Slice Type (Output)

To create ```filtereddata.txt```, you likely transformed specific columns from the Excel sheet into a more compact numerical representation. 
Here’s a breakdown of how each column in ```filtereddata.txt``` could correspond to columns in the Excel file:

**Column Mappings:**

- Use CaseType (Input 1): Since the sample data shows only "Smartphone", it is mapped to 1.
- LTE/5G UE Category (Input 2): This is directly taken as is (1, 2, 3, etc.).
- Technology Supported (Input 3): Since the sample data shows only "LTE/5G", it is mapped to 1.
- Day (Input 4): The days of the week are mapped to numbers, with "Monday" as 0, "Tuesday" as 1, and so on.
- Time (Input 5): This is directly taken as is (0, 1, 2, etc.).
- QCI (Input 6): This is directly taken as is (2, 5, etc.).
- Packet Loss Rate (Reliability): Assumed to be 1 for the value 0.01.
- Packet Delay Budget (Latency): The value "<50ms" is mapped to 5.
- Slice Type (Output): Since the sample data shows only "eMBB", it is mapped to 1.

**Constructing the Filtered Data:**

- Each row in filtereddata.txt corresponds to a row in the Excel file with the mapped numerical values.
- The structure of each row is consistent with the following order of columns:

1. Use CaseType (Input 1)
2. LTE/5G UE Category (Input 2)
3. Technology Supported (Input 3)
4. Day (Input 4)
5. Time (Input 5)
6. QCI (Input 6)
7. Packet Loss Rate (Reliability)
8. Packet Delay Budget (Latency)
9. Slice Type (Output)

**Example Mappings:**

![image](https://github.com/user-attachments/assets/3096158f-5159-482b-b8fc-f7f1887eb744)

Thus, the first row 1,1,1,1,0,2,1,5,1 in filtereddata.txt translates back to the original data as follows:

- 1 (Use CaseType) = "Smartphone"
- 1 (LTE/5G UE Category) = 1
- 1 (Technology Supported) = "LTE/5G"
- 1 (Day) = "Monday"
- 0 (Time) = 0
- 2 (QCI) = 2
- 1 (Packet Loss Rate) = 0.01
- 5 (Packet Delay Budget) = "<50ms"
- 1 (Slice Type) = "eMBB"
  
Each subsequent row follows the same mapping logic. By understanding this, we can recreate the filtered data from the Excel sheet or verify if additional unique mappings are involved for other values.

## Applications
1. **Optimal Resource Allocation:** The model predicts optimal resource allocations for different network slices based on current network conditions. This can include dynamically adjusting bandwidth, latency, and security parameters to meet the specific needs of applications running on each slice.
2. **Real-time Adaptation:** During runtime, the model continuously evaluates incoming data and makes predictions to adapt network slices in real-time. This ensures that resources are efficiently utilized and applications receive the necessary quality of service (QoS).
3. **Scenario Testing:** Users can simulate various scenarios (e.g., high traffic, low latency requirements) using the demo interface. The model provides insights into how network slices perform under different conditions, helping users understand the benefits of network slicing in optimizing network resources.
4. **Decision Support:** Network administrators and operators can use the demo to make informed decisions about network configurations and optimizations. Insights provided by the deep learning model can guide strategic planning and resource allocation strategies in 5G deployments.

