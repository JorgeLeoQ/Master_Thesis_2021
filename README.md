<h1><b>Design, Implementation and Testing of Deep Learning-Based Driving Scenario Classifiers for Automated Vehicles</b></h1>

The goal of this project is to design, implement, and evaluate the performance of different neural network architectures for driving scenario classification.

The first implemented networks are two versions of residual 3D convolutional networks:
- The first one (R3D) uses fully 3D convolutional kernels.
- The second one (R(2+1)D) separates, within each residual block, the 2D spatial convolution from the 1D temporal convolution.

Finally, a (YOLOP + CNN) + LSTM architecture was developed, which processes each frame spatially only once (rather than every time it appears within a sliding analysis window), aiming to achieve latency compatible with real-time driving scenario analysis.

The networks were tested on a synthetic dataset comprising four simple classes (approaching a static leading vehicle, lane change, following a leading vehicle, and free ride) under three different conditions (day, night, and rain with fog).

<h2><b>Network Architectures</b></h2>

The three network models were implemented using PyTorch and TensorFlow:

![R(2+1)D and R3D structure](images/RCN.png?raw=true "Figure 1")

![(YOLOP + CNN) + LSTM structure](images/(YOLOP_+_CNN)_+_LSTM.png?raw=true "Figure 2")

<h2><b>Dataset</b></h2>

A synthetic dataset was generated using the CARLA simulator:

![Approaching static leading vehicle](images/Approach.gif?raw=true "Figure 3")
![Change lane](images/changelane.gif?raw=true "Figure 4")
![Following leading vehicle](images/follow.gif?raw=true "Figure 5")
![Free ride](images/freeride.gif?raw=true "Figure 6")

Example of a dataset sample processed with YOLOP:

![Example of sample of previous dataset processed with YOLOP](images/YOLOP_sample.GIF?raw=true "Figure 7")

<h2><b>Results</b></h2>

The experimental results suggest two potential use cases for the tested networks:  
- *Offline*:
  - R(2+1)D performs better in rapidly changing scenarios or when low latency is required.
  - R3D is more suitable for slowly evolving scenarios or those with lower FPS.
- *Online*:
  - (YOLOP + CNN) + LSTM stack is more appropriate for real-time inference.

<h2><b>Static Analysis</b>: Confusion Matrix (Full Video)</h2>

These are the confusion matrices generated from full video classification using each of the three neural networks:

![R(2+1)D confusion matrix (full video)](images/8sec_(2+1)D.png?raw=true "Figure 3") 
![R3D confusion matrix (full video)](images/8sec_3D.png?raw=true "Figure 8") 
![(YOLOP + CNN) + LSTM confusion matrix (full video)](images/8sec_YOLOP.png?raw=true "Figure 9")

<h2><b>Dynamic Analysis</b> (Clips of Varying Length and Conditions)</h2>

Graphs showing the classification performance of the different neural networks under various weather and lighting conditions:

![R(2+1)D](images/acc_2+1d.png?raw=true "Figure 6") 
![R3D](images/acc3d.png?raw=true "Figure 10") 
![(YOLOP + CNN) + LSTM](images/accYOLOP.png?raw=true "Figure 11")

<h2><b>Accuracy and Precision with Varying Number of Training and Testing Frames</b></h2>

Residual convolutional neural networks tested with 2-second video clips:

![R(2+1)D and R3D](images/Accuracy_and_Precision.png?raw=true "Figure 12")

(YOLOP + CNN) + LSTM tested with 4-second video clips:

![(YOLOP + CNN) + LSTM](images/Accuracy_and_Precision_YOLOP.png?raw=true "Figure 13")

<h2>Inference Time Performance</h2>

![R(2+1)D time inference](images/tR(2+1)D.png?raw=true "Figure 11") 
![R3D time inference](images/tR3D.png?raw=true "Figure 14") 
![(YOLOP + CNN) + LSTM time inference](images/tYOLOP.png?raw=true "Figure 15")

<h2>Requirements</h2>

See `requirements.txt`

<h2><b>Technologies Used</b></h2>

- **Programming languages**: Python
- **Deep learning frameworks**: PyTorch, TensorFlow
- **Computer vision**: OpenCV, YOLOP (You Only Look Once for Panoptic tasks)
- **Simulation environment**: CARLA Simulator
- **Data processing**: NumPy, Matplotlib, Scikit-learn
- **Visualization**: Matplotlib, GIFs/Images
- **Model evaluation**: Confusion Matrix, Accuracy, Precision, Inference Time

<h3><b>Acknowledgements</b></h3>

[YOLOP](https://github.com/hustvl/YOLOP)  
[R(2+1)D](https://github.com/irhum/R2Plus1D-PyTorch)

<h3><b>Additional Information</b></h3>

This project was developed as part of the Master’s Thesis by Alessandro [YourLastName] and Marianna Cossu.  
It led to the publication of the report *“Classifying Simulated Driving Scenarios from Automated Cars”*, presented in September 2021 at the University of Pisa.  
🔗 [Link to the publication](https://www.springerprofessional.de/en/classifying-simulated-driving-scenarios-from-automated-cars/20297592)

⚠️ The source code is not publicly available as it is property of the University of Genoa.
