Human Activity Recognition (HAR) Project
Overview
This project develops and evaluates deep learning models for human activity recognition (HAR) using the AReM dataset. Activities are classified based on multi-sensor data, including accelerometer and Received Signal Strength (RSS) readings. The project employs LSTM, CNN, and Transformer architectures, with preprocessing and augmentation steps tailored to improve model generalization and accuracy.

Key Features
Dataset: AReM dataset, featuring six human activities.
Models: LSTM, CNN, and Transformer architectures designed for time-series data.
Data Augmentation: Techniques like Gaussian noise, time shifting, and sequence normalization.
Evaluation: Comprehensive metrics for accuracy, precision, recall, and F1-score.
Dataset
AReM Dataset: Contains sensor data for six activities:

Bending
Lying Down
Sitting
Standing
Walking
Cycling
Each activity's data is provided in CSV files organized by activity type.

Steps Followed in the Paper
1. Data Preprocessing
Data Loading:
CSV files for each activity were loaded and concatenated into a single DataFrame.
Rigorous error handling was applied to clean corrupted files.
Cleaning:
Removed non-numeric values and NaN entries.
Verified data types for consistency.
Standardization:
Applied StandardScaler to normalize features such as avg-rss12 and var-rss12 to have a mean of zero and a standard deviation of one.
Label Encoding:
Converted activity labels into integer codes using LabelEncoder.
Sequence Segmentation:
Transformed data into fixed-length sequences of 50 time steps to meet the input requirements of deep learning models.
2. Data Augmentation
Gaussian Noise: Added noise (std = 0.1) to simulate real-world sensor variability.
Time Shifting: Shifted sequences randomly by up to ±5 time steps to account for timing irregularities.
Padding and Trimming: Ensured all sequences had a fixed length of 50 time steps.
3. Model Architectures
LSTM Model:
Captured temporal dependencies in time-series data.
Included dropout layers (rate = 0.5) for regularization.
Outputs processed through a dense layer for activity classification.
CNN Model:
Extracted spatial features using three convolutional layers (filters: 32, 64, 128).
Max pooling reduced dimensionality while retaining key features.
Dense layers converted extracted features into activity predictions.
Transformer Model:
Used TimeSeriesPatchEmbeddingLayer to process data into patches.
Positional encodings preserved temporal relationships.
Self-attention mechanisms captured global dependencies.
Final dense layer assigned activity labels.
4. Training
Dataset split into:
60% Training
20% Validation
20% Testing
Optimizer: Adam optimizer with a learning rate of 0.001.
Loss Function: Cross-Entropy Loss for multi-class classification.
Metrics (loss, accuracy) monitored throughout training for optimization.
5. Evaluation
Models compared based on:
Accuracy: Overall and for individual activities.
Precision, Recall, and F1-Score: To assess classification performance.
Ten independent runs averaged to ensure robust performance metrics.
6. Results
Transformer: Achieved highest accuracy (98.4%) due to attention mechanisms and positional encodings.
LSTM: Effective for sequence-based tasks, with 96.9% accuracy.
CNN: Demonstrated strong spatial feature extraction, with 96.4% accuracy.
Data augmentation improved model generalization and performance metrics.
Inputs and Outputs
Inputs
Raw Data: CSV files for six activities from the AReM dataset.
Preprocessed Data: Cleaned and augmented sequences.
Parameters:
StandardScaler for normalization.
Gaussian noise (std = 0.1).
Sequence length: 50 time steps.
Outputs
Predictions: Activity classifications for each input sequence.
Performance Metrics:
Accuracy
Precision, Recall, F1-Score
Validation Loss and Accuracy
Comparison Visualizations:
Model performance across metrics and activities.
