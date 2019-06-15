## Speech Denoising using DNN

There were 2 audio files such as 'train_dirty_male.wav' and 'train_clean_male.wav' which were used for training. train dirty male.wav and
train clean male.wav are the noisy speech and its corresponding clean speech you are going to use for training the network. These files were first convertd into spectrograms using STFT to get 'S' (clean) and 'X' (noisy) matrices. Taking their magnitudes by using np.abs() 
because S and X are complex valued.

Then training a fully-connected deep neural network using 4 hidden layers. The input to the network is a column vector of |X| (a 513-dim vector) and the target is its corresponding one in |S|. 

Once the training was completed, the model was tested on 'test_01_x.wav' and 'test_02_x.wav' files. ISTFT was applied on the output of the network to convert the matrices into time domain. Signal-to-Noise Ratio (SNR) was also calculated to check the quality of the output generated.