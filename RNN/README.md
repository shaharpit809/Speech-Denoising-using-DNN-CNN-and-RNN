## Speech Denoising using LSTM

In this project, I take a dataset of 3600 audio files from which 1200 audio files of clean, noisy and mixed speech each. I trained the RNN to remove the noisy signal from the mixed audio files to get clear audio files. First, we will perform STFT and take the magnitude of all the files such that we get 3 lists such as |S| , |N| and |X| for clean, noisy and mixed respectively. 

The |X| list will be the input to the LSTM model (consisting of LSTM cells) and the target will be Ideal Binary Masks (IBM) matrix which can be computed from clean and noisy speech signal using the below formula: \
![]()

IBM assumes that each of the time-frequency bin at (f; t), an element of the |X| matrix, is from either speech or noise. Although this is not the case in the real world, it works like a charm most of the time by doing this operation: \
![]()

Eventually, the LSTM model will learn a function that approximates the 'M' matrix.

Once the training was completed, I checked the performance of the model on a validation set and managed to get an average SNR of 10 dB. I also tested the performance of the model on test audio files and after listening to the reconstructed audio files, I can confidently say that the LSTM model performed fairly well.

Since the dataset is large, I haven't uploaded it yet. Please let me know if you need the input files and also the output files (reconstructed audio files) to check the performance of the code.