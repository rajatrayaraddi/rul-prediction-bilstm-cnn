# Remaining Useful Life Prediction with BiLSTM-CNN Hybrid Model

This repository contains code and experiments for predicting the Remaining Useful Life (RUL) of turbofan engines using a hybrid deep learning model that combines BiLSTM, CNN, and attention mechanisms. The project is based on the NASA C-MAPSS dataset and includes preprocessing, model training, evaluation, and hyperparameter tuning.

## 📁 Repository Structure

- `lstmcnn.ipynb`: Main notebook containing the preprocessing pipeline, model architecture, training, evaluation, and visualizations.
- `hyperparameter_tuning.ipynb`: Contains code for hyperparameter tuning using Keras Tuner.
- `architecture_experiments.ipynb`: Standalone experiments with alternative architectures (e.g., TCN, standalone LSTM).
- `weights/`: Pretrained model weights for each subset (FD001, FD002, FD003, FD004).
- `keras_tuner_trials.csv`: Results from hyperparameter tuning trials.

---

## 🚀 How to Run

1. **Download the C-MAPSS Dataset**:
   - Place the original C-MAPSS dataset files inside a folder named `CMAPSS`.
   - Update the `dir_path` variable in the `get_data()` function (Cell 2 of `lstmcnn.ipynb`) with the correct path.

2. **Choose Dataset Subset**:
   - Set the desired subset (e.g., `'FD001'`, `'FD002'`, etc.) in the `dataset` variable in Cell 3.

3. **Run Notebook**:
   - Execute all cells in sequence.

4. **Important Note on Model Training**:
   - Only run the **model compilation and training block** for the dataset subset you selected.
   - Each subset has its own block; choose accordingly.
   - To skip full training and view results quickly, you may set `epochs=1`.

5. **Viewing Saved vs. Current Model Results**:
   - By default, saved weights are loaded after training.
   - To use weights from current training instead, **comment out the `model.load_weights()` line**.

---

## 📊 Visualizations

The following plots are generated in `lstmcnn.ipynb`:
- True vs. Predicted RUL
- Prediction Error Distribution
- Prediction Error by Engine Units
- Model architecture diagrams

---

## 🧠 Notes on Model Saving

Model saving via `model.save()` and reloading with `load_model()` is currently **not supported** due to the use of a custom `PositionalEncodingLayer`. Although the layer includes proper configuration methods, it is not recognized during deserialization. This issue is actively being worked on.

---

## 🧪 Training Time (Google Colab, T4 GPU)

| Subset | Approx. Training Time |
|--------|------------------------|
| FD001  | ~2 minutes             |
| FD002  | ~4 minutes             |
| FD003  | ~2 minutes             |
| FD004  | ~7 minutes             |

---

## 📜 License

This project is released under the [MIT License](LICENSE).
