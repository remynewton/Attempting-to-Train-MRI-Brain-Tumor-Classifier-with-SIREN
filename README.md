Recently I learned about SIRENs - sinusoidal representation networks - and I was absolutely amazed by their ability to take signals, such as images, audio files, etc., and create nearly perfect functions mapping them to their values. It also matches the derivativess of the signals (i.e. edge detection) incredibly well. (Check out some cool examples at: https://www.vincentsitzmann.com/siren/) They achieve this by using a sinusoidal activation function, which are very good at capturing natural signals (e.g. as in the age old fourier sine transform), but are sadly not monotonic due to their periodicity. Sitzmann, et. al. got past this problem by initializing the weights very carefully; they ended up using He Uniform initialization. You can read more about it at: https://arxiv.org/pdf/2006.09661.pdf.

Anyway, I found a university team who trained a CNN on a pretty small dataset of MRI images for the binary classification of the presence or absence of tumors in the aforementioned images. (You can see their video presentation at: https://www.youtube.com/watch?v=sR-2KXuaQRw) I wondered if I could get even higher accuracy on the test set than them by using a SIREN. Initially, a small SIREN didn't really seem to do as well, so then I decided to implement transfer learning by training a VGG16 SIREN on the CIFAR-10 dataset and then combining part of that model with a much smaller one to train on the MRI brain tumor dataset. The VGG16 SIREN training went pretty well.
