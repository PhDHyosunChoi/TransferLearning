citation key: nanniEnsembleConvolutionalNeural2021b
## Summary and Tagging: 

In this paper, we presented the largest study conducted so far that investigates #ensembles of #CNNs using different #data-augmentation techniques for #audio #classification. 

Data augmentation methods were applied to the raw audio signals and their #visual #representations using different #spectrograms. CNNs were trained on different sets of data augmentation approaches and #fused via the sum rule.

Most studies in this area have focused on #extracting handcrafted texture #features from #visual-representations of #sound [58]. But recently, there has been some interesting work that has successfully used #deeplearning to solve this problem [57].

To the best of our knowledge, this is the largest, most exhaustive study of CNN ensembles applied to the task of #audio-classification. 


1.  Introduction 
	- Most early work in sound classification began by extracting features from audio recordings such as the Statistical Spectrum Descriptor or Rhythm Histogram [5].
	- Visual representations of audio, such as spectrograms [6] and Mel-frequency Cepstral Coefficients spectrograms (Mel) [7], contain valuable information, powerful texture extraction techniques like local binary patterns (LBP) [8] and its many variants [9]began to be explored for audio classification [2,10].
	- Recently, deep learners have proven even more robust in image recognition and classification than have texture analysis techniques.
	- In both these works, the authors combined CNN with visual features; the fusion of CNNs with traditional techniques was shown to outperform both the stand-alone conventional and single deep learning approaches.
	- Another environmental audio recognition problem that is growing in relevancy has to do with identifying sources of noise in environments.
	- For all its power, deep learning also has significant drawbacks when it comes to environmental sound classification. For one, deep learning approaches require massive training data [22].
	- Fortunately, there are methods for increasing the number of images in small datasets. One such method is to apply data augmentation techniques.
	- Audio signals can be augmented in both the time and frequency domains, and these augmentation techniques can be directly applied either on the raw signals themselves or on the images obtained after they have been converted into spectrograms.
	- This augmentation process not only enlarged the dataset but also produced nearly a 10% improvement in identification performance. Similarly, some standard audio augmentation techniques such a time and pitch shifts for bird audio classification were applied in [24].
	- This summing technique was used for domestic sound classification in [25,26].
	- The goal of this work is to perform an extensive study of CNN classification using different architectures combined with an investigation of multiple sets of different data augmentation approaches and methods for representing audio signals as images.
	- The main contribution of this study is the exhaustive tests performed on ensembles made by fusing (see Figure 1) five CNNs trained with four audio representations of raw sound signals combined with six different data augmentation methods (totaling thirty-five subtypes).

2. Audio Image Representations
		2-1. The Discrete Gabor Transform (DGT)
		2-2. Mel spectrograms (MEL) [36]
		2-3. Gammatone (GA) band-pass filters
		2-4. Cochleagram (CO)
		- Each of the four spectrograms is then mapped to a gray-scale image using a linear transformation that maps the minimum value to 0 and the maximum value to 255, with the value of each pixel rounded to the closest smaller integer.

3. Convolutional Neural Networks (CNNs)

4. Data Augmentation Methods
		4-1. Standard Signal Augmentation (SGN)
		4-2. Short Signal Augmentation (SSA)
		4-3. Super Signal Augmentation (SSiA)
		4-4. Time-Scale Modification (TSM)
		4-5. Short Spectrogram Augmentation (SSpA)
		4-6. Super Spectro Augmentation (SuSA)
	

5. Results
	- Also, it should be noted that many papers [16,27,46,48,51–53] report classification results on the datasets listed above that are superior to human performance.
	- We combined the results of the CNNs in an ensemble using the sum rule. The sum rule consists of averaging all the output probability vectors of the stand-alone CNNs in the ensemble to create a new probability vector that is used for classification.  
	- The rationale behind fusion, as Hansen [31] notes, is that "the collective decisopn produced by the ensemble is less likely to be in error than the decision made by any of the individual networks." 
	- In Table 6, our best ensembles FusionGlobal and FusionGlobal-CO are compared with the state of the art.
	- The following conclusions can be drawn from the reported results:
		1. There is no single data augmentation protocol that outperforms all the others across all the tests. TSM performs best on CAT and ESC-50 but works poorly on BIRDZ. Data augmentation at the spectrogram level works poorly on ESC-50 as well as on two other datasets. SGN and data augmentation at the signal level work well across all the datasets. On average, the best data augmentation approach is SSA. Although it produces a performance that is close to SSiA, the training time for SSA is shorter;
		2. The best stand-alone CNNs are VGG16 and VGG19;
		3. DGT works better than the other signal representations;
		4. Combining different CNNs enhances performance across all the tested datasets;
		5. For the ensemble FusionLocal, data augmentation is marginally beneficial on CAT and BIRDZ but produces excellent results on ESC-50. Compared to the stand-alone CNNs, data augmentation improves results on all three datasets. Of note, an ensemble of VGG16 (FusionSuperVGG16) outperforms the stand-alone VGG16;
		6. The performance of the ensemble of CNNs trained with different augmentation policies (FusionALL) can be further improved by adding to the ensemble those networks trained using different signal representations (FusionGlobal). However, this performance improvement required considerable computation time, mainly during the training step;
		7. The approach in [20] manages to outperform our results, but the authors pretrained their networks on AudioSet; hence the comparison with our approach is not fair.


6. Conclusions
	- In this paper, we presented the largest study conducted so far that investigates ensembles of CNNs using different data augmentation techniques for audio classification. 
	- Data augmentation methods were applied to the raw audio signals and their visual representations using different spectrograms. CNNs were trained on different sets of data augmentation approaches and fused via the sum rule.
	- Experimental results clearly demonstrate that ensembles composed of fine-tuned CNNs with different architectures maximized performance on the tested three audio classification problems, with some of the ensembles obtaining results comparable with the systems, including on the ESC-50 dataset. To the best of our knowledge, this is the largest, most exhaustive study of CNN ensembles applied to the task of audio classification. Our best ensemble, FusionGlobal is composed of 63 networks with nine different architectures and seven different trainings for every network. Four of the networks were obtained using different data augmentation strategies and three different methods to create a spectrogram.
	- This work can be expanded further by investigating which augmentation methods(spectrogram augmentation vs. signal augmentation) work best for classifying different kinds of sounds. We also plan to apply transfer learning using spectrograms instead of natural images. A systematic selection of augmentation approaches, e.g., by iteratively evaluating an increasing subset of augmentation techniques (as is typical when evaluating different features), would require an enormous amount of time and computation power.
	- Furthermore, there is a need to investigate the impact on performance when different CNN topologies and parameter settings in the retuning step are combined with different types of data augmentation.
	- Most studies in this area have focused on extracting handcrafted texture features from visual representations of sound [58]. But recently, there has been some interesting work that has successfully used deep learning to solve this problem [57].
	- combining a different set of network architectures, but the main idea of ensembling different models obtained from many audio augmentation protocols should increase classification performance on these novel tasks and would be worth investigating in the future. Finally, we plan on exploring some possibilities presented in [59].