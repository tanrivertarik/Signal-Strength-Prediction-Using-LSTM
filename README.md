

---

# 📡 Signal Strength Prediction Using LSTM

## Overview
This project focuses on predicting the LTE signal strength (RSRP) using a deep learning model. By leveraging an LSTM (Long Short-Term Memory) network, the model learns from historical signal data and various features like location, time, and speed to forecast future signal quality. This prediction can aid in optimizing mobile network infrastructure, improving connectivity, and enhancing user experience.

## Dataset
The dataset used for this project consists of various LTE signal parameters collected over time, including:
- **Timestamp**: The date and time of each recorded signal measurement.
- **Longitude** and **Latitude**: GPS coordinates of the measurement location.
- **Speed**: Speed of the user or device at the time of recording.
- **RSRP (Reference Signal Received Power)**: Key measure of signal strength in LTE networks.
- **RSRQ (Reference Signal Received Quality)**: Indicates the quality of the received signal.
- **SNR (Signal-to-Noise Ratio)**: Reflects the quality of the signal in relation to background noise.
- **ServingCell_Distance**: Distance between the device and the serving cell tower.
- **Hour** and **DayOfWeek**: Temporal features extracted from the timestamp.

## Methodology
### 1. **Data Preprocessing**
- Converted timestamps into temporal features (`Hour` and `DayOfWeek`).
- Cleaned non-numeric values and interpolated missing values.
- Normalized features to scale values for the neural network.
- Created sequences of fixed length (e.g., 10 past samples) to serve as input for the LSTM model.

### 2. **Model Architecture**
The model is based on a multi-layer LSTM (Long Short-Term Memory) network:
- **Layer 1**: LSTM layer with 32 units, configured to return sequences for the next layer.
- **Layer 2**: Dropout layer to prevent overfitting.
- **Layer 3**: LSTM layer with 16 units, configured to return a single output.
- **Layer 4**: Dropout layer.
- **Output Layer**: A Dense layer with a single unit for regression (predicting RSRP).
  
The model is compiled with the Mean Squared Error (MSE) loss function and trained using the Adam optimizer.

### 3. **Model Training and Evaluation**
- The model was trained for 5 epochs with a batch size of 16 on the preprocessed dataset.
- During training, both training and validation losses were monitored to track the model's performance.
- The final model achieved a Root Mean Squared Error (RMSE) of approximately 0.08, indicating a relatively good predictive performance.

## Analysis and Visualizations
### 1. **Actual vs. Predicted Signal Strength**
A plot comparing the actual and predicted signal strength values across the test dataset shows that the model generally follows the trend of the actual signal strength, with some discrepancies.

### 2. **SNR and Speed Analysis**
Further analysis of specific segments in the data, especially those showing significant drops in signal strength, revealed the following:
- Fluctuations in **SNR** values contributed to signal strength variability.
- Changes in **Speed** might also impact signal strength due to handovers and fading effects.

### 3. **Visualizations**
This project includes several visualizations:
- **Training and Validation Loss**: Shows the model's learning process over epochs.
- **Scatter Plot**: Compares actual vs. predicted values.
- **Residuals Plot**: Shows the distribution of prediction errors.
- **SNR and Speed Analysis**: Identifies potential factors contributing to signal drops.

## How to Use
### Prerequisites
- Python 3.x
- Required packages: `numpy`, `pandas`, `matplotlib`, `tensorflow`, `sklearn`, `seaborn`, `shap` (optional for feature importance)

Install the dependencies using:
```bash
pip install numpy pandas matplotlib tensorflow scikit-learn seaborn shap
```

### Running the Project
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/tanrivertarik/Signal-Strength-Prediction-Using-LSTM.git
   ```
   
2. **Prepare the Dataset**:
   - Place your dataset (`combined_LTE_data.csv`) in the project directory.

3. **Run the Main Script**:
   - Open the Jupyter notebook or Python script provided in the repository (`main.py`).
   - Execute the script to preprocess the data, train the model, and generate visualizations.

### Usage Notes
- Modify the `sequence_length` and model parameters to experiment with different configurations.
- Analyze specific segments in the data using the visualization tools provided.

## Results
The final model demonstrates the potential to predict LTE signal strength based on historical data. Further improvements, such as hyperparameter tuning, additional feature engineering, and more advanced models (e.g., attention mechanisms), could enhance the predictive accuracy.

## Contributing
Contributions are welcome! Feel free to open issues or submit pull requests for improvements, new features, or bug fixes.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.

## Contact
For questions, please reach out to tarikktanriver@gmail.com or connect with me on [LinkedIn](https://www.linkedin.com/in/tanrivertarik/).
