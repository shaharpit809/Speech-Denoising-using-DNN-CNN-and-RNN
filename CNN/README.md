## Speech Denoising using 1D CNN

In this problem, I have implemented a 1D CNN that does speech denoising in the STFT magnitude domain. 1D CNN here means a variant of CNN which does the convolution operation along only one of the axis. In this case it's the frequency axis. Taking transpose of this STFT matrix, so
that each row of the matrix acts as a spectrum. So the 1D CNN takes one of these row vectors as an example coupled with the 'B' minibatch size. After deciding on the minibatch size, I defined 'K' kernels. Since the output matrix should be of size [B x 513], the dimensions of CNN was very high dimensional so I performed maxpooling and added a fully connected layer at the end to reduce the dimensionality and get the desired dimensions. 

After training the model, I tested the performance of the model by calculating the Signal-to-Noise Ratio (SNR) value and performed ISTFT to check how the audio sounded. 

## Speech Denoising using 2D CNN

In this problem, since we are using a 2D CNN, we will consider both time and frequency of the audio. After applying STFT on the input audio files, I first take a matrix of [20 x 513] out of the entire STFT magnitude spectrogram (transposed). That's an input sample. Using this the 2D CNN estimates the cleaned-up spectrum that corresponds to the last (20th) input frame: \
![https://github.com/shaharpit809/Speech-Denoising-using-DNN-CNN-and-RNN/blob/master/img/2D_CNN_eqn1.PNG]()

What it means is, the network takes all 20 current and previous input frames into account to predict the clean spectrum of the current frame, t + 19.
Likewise, the next maxtrix will be another 20 frames shifted by one frame such that 19 frames overlap with the previous one. Since the original STFT spectrogram has 2,459 frames, we can create 2,440 such images as the training dataset.

Since we are using a 2D CNN, the kernel size will also be in 2D such that both the width (frequencies) and the height axes (frames) be larger than 1.

Once the model is built, we can test its performance on the test audio by calculating SNR and listening to check if the noise is removed or not. 