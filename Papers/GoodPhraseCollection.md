-------------------------
## Abstract
```
We describe a system for robustly estimating synthetic depth maps in unconstrained images and videos, for semi-automatic conversion into stereoscopic 3D.
我们描述一个。。。系统
We generate good quality content, more suitable for perception, compared to a similar framework.
我们获得。。。
In this paper, we propose ...
For this work, we propose ...
This paper introduces a new ...
本文提出了。。。。
The proposed ... achieves improvement up to 0.8 dB from the experimental results.
根据实验结果，本文方法可以达到。。。
we introduce the first depth from focus (DfF) method capable of handling images from mobile phones and other hand-held cameras.
我们提出。。。
Achieving this goal requires solving a novel uncalibrated DfF problem and aligning the frames to account for scene parallax.
为了实现这个目标需要解决。。。
Our approach is demonstrated on a range of challenging cases and produces high quality results.
我们的方法在。。。得到证明
We present an approach to dense depth estimation from a single monocular camera that is moving through a dynamic scene.
我们提出了一个。。。的方法。
We provide a novel motion segmentation algorithm that segments the optical flow field into a set of motion models, each with its own epipolar geometry.
我们提供一个新的。。。方法。
Experimental results demonstrate that the presented approach outperforms prior methods for monocular depth estimation in dynamic scenes.
实验结果证明。。。
Learning based methods have shown very promising results for the task of depth estimation in single images. However, most existing approaches treat depth prediction as a supervised regression problem and as a result, require vast quantities of corresponding ground truth depth data for training.
。。。的方法被广泛使用。。。。然而，目前很多方法。。。。
In this paper, we innovate beyond existing approaches, replacing the use of explicit depth data during training with easier-to-obtain binocular stereo footage.
本文中我们提出了一种替代超过已有方法的新思路。。。。
By exploiting epipolar geometry constraints, we generate disparity images by training our networks with an image reconstruction loss.
通过发掘。。。。我们。。。
To overcome this problem, we propose a novel training loss that enforces consistency between the disparities produced relative to both the left and right images, leading to improved performance and robustness compared to existing approaches.
为了解决这个问题。。。。
Our method produces state of the art results for monocular depth estimation on the KITTI driving dataset, even outperforming supervised methods that have been trained with ground truth depth.
我们的方法获得了最好的结果。。。。。
```

## Introduction
```
As a consequence, not only does it yield temporal smoothness, but it also helps improving the accuracy of depth boundary estimation.
所以，该方法不仅可以获得。。。而且可以提高。。。
An example of what a depth map can look like is shown in Fig. 1 below. 
关于。。的一个例子可以由下图来表示。
The core of our system combines the merits of two semi-automatic segmentation algorithms to produce high quality depth maps: Random Walks and Graph Cuts.
我们系统的核心结合了。。。的优点。。。
This paper presents the first successful demonstration of this capability, which we call hand-held DfF.
本文提出了。。。
By exploiting a densely-sampled focal stack, we propose a simpler alignment technique based on flow concatenation.
通过。。。我们提出了。。。
We address the hand-held DfF problem in two steps:
我们分。。步处理。。问题。。。
To solve this problem, we first compute an all-in-focus photo using an MRF-based approach.
为了解决这个问题，我们。。。
To support challenging field applications, a monocular depth reconstruction approach should have a number of characteristics
为了解决充满挑战领域里的问题，一个。。方法应该。。。
Our approach comprises two stages. The first stage...
我们的方法由两部分组成，第一部分。。。
Our algorithm supports dense segmentation of complex dynamic scenes into possibly dozens of independently moving components.
我们的算法支持。。。。
The main insight is that moving objects do not exist in a vacuum, but fulfill intrinsic occluder-ocludee relationships with respect to each other and the static environment.
主要的想法在于。。。
We formulate this reconstruction problem as continuous optimization over scales and depths and introduce ordering and connectivity constraints to assemble the scene
我们将这种。。问题作为。。。
We evaluate the presented approach on complex dynamic sequences from the challenging Sintel and KITTI datasets.
我们通过。。。来衡量我们的算法。。。
In this work, we take an alternative approach and treat automatic depth estimation as an image reconstruction problem during training.
本工作中，我们采用另外一种思路来。。。。
Specifically, we propose the following contributions:
特别地，我们提出了以下贡献。。。。
```

## Related Work
```
Despite these problems, this is a very important part of the stereoscopic post-processing process, and should not be dismissed.
尽管有这些问题。。。
Research into conversion techniques is on-going, and most currently focus on generating a depth map, which is a monochromatic image of the same dimensions as the image or frame to be converted.
关于。。的研究仍在进行中，并目前正在关注。。。
Recent research in 2D to stereoscopic 3D conversion include the following, each concentrating on a particular feature or approach to solve the problem.
近期关于。。。的研究包含以下几个方面，每个方面关注一个特定的方面来解决该问题。
The idea is that for objects closer to the camera, they should move faster, whereas for objects that are far, they should be slower.
该观点是。。。
At the present time, most conversion methods focus on extracting depth automatic automatically.
目前，大部分方法重点关注。。。
One question often arising is whether or not the depths that the user mark are indeed the right ones for perception in the scene.
存在的一个问题是。。。
In addition, this method could not be used in specifying depths on background areas, as the core of the algorithm relies on separation between the background and foreground by strong edges. 
此外，该方法不能。。。
Upon closer inspection, we can consider semi-automatic 2D to 3D conversion as a multi-label image segmentation problem.
经过仔细观察，我们可以认为。。。
Inspired by Guttmann et al., we propose a stereoscopic conversion system to create depth maps for 2D to 3D conversion.
受到。。。的启发，我们提出了。。。。
It is natural to assume that marking several keyframes over video is time consuming.
很自然的认为。。。
In this aspect, we allow the user the choice of which keyframes to mark.
在这方面。。。
In this paper, we first discuss the general framework for the conversion of images. After, we consider video, investigating methods for minimizing user effort in label propagation. We also show
sample depth maps and anaglyph images, and compare our efforts to [12], demonstrating that our approach is more preferable for human perception.
在本文中，我们首先讨论。。。，然后，。。。我们也展示了。。。，我们的结果。。。。
However, none of these techniques address parallax, and therefore fail for hand-held image sequences.
然而，这些工作中没有考虑。。。
Three significant families of approaches have been proposed for estimating dynamic scene geometry from monocular video. 
目前主要有三种的方法族用来解决。。。问题
We briefly review each approach in turn.
我们依次回顾每类算法。
This approach is based on the assumption that the environment consists of multiple rigidly moving objects.
这个方法是基于这样的假设。。。
This approach typically assumes a small set of rigid objects in the scene and has not produced detailed reconstructions of complex scenes with non-rigidly moving objects.
这个方法通常假设。。。。
The basic idea is to cluster feature tracks and fit rigid motion models to each cluster.
主要的观点是。。。
In contrast, our approach estimates dense depth for complex dynamic scenes over the entire visual field.
相比之下，我们的方法。。。
This approach relies on the availability of a dataset of color-depth image pairs at test time.
这种方法是基于。。。。
This approach requires the availability of an appropriate dataset with ground-truth depth data at test time.
这种方法需要。。。
In contrast, we present a geometric method that does not require a training dataset and naturally applies to novel environments.
相比之下，我们提出了一种方法。。。
However, most of these techniques rely on the assumption that multiple observations of the scene of interest are available.
然而，大多数方法都依赖于这样的假设。。。。
To overcome this limitation, there has recently been a surge in the number of works that pose the task of monocular depth estimation as a supervised learning problem.
为了超越这个限制，。。。。。
Concurrently to this work, there are some existing methods that also address the same problem. But those have several limitations e.g. they are not fully differentiable, making training suboptimal [11], or they have image formation models that do not scale to large output resolutions [9].
对于这个工作，已经有很多算法来解决这个问题，例如。。。但是它们都有一定的限制。。。。
We improve upon these methods with a novel training objective and enhanced network architecture, to significantly increase the quality of our final results.
我们通过。。。。提升了这些算法。。。
There is a large body of work that focuses on depth estimation from images, either using pairs.....
已经有很多方法关注。。。。这个领域，。。。。
Here we focus on works related to monocular depth estimation, where there is only a single input image....
目前我们主要关注。。。。。
Recently, it has been shown that instead of using hand defined similarity measures, treating the matching as a supervised learning problem and training a function to predict the correspondences produces far superior results[17], [18]..
近来，人们发现。。。可以。。。
A drawback of this approach is that it relies on the entire dataset being available at test time.
该方法的一个缺点是。。。。
Eigen et al. [2], [27] showed that it was possible to produce dense pixel depth estimates using a two scale deep network, trained on images and their corresponding depth values.
。。。发现。。。。。。
In this work, we perform a comparison to the Deep3D image formation model, and show that our algorithm produces superior results.
本文中，我们与。。。方法进行比较。。。
Here we focus on works related to monocular depth estimation
这里我们主要关注。。。。
Recently, it has been shown that instead of using hand defined similarity measures, treating the matching as a supervised learning problem and training a function to predict the correspondences produces far superior results.
最近，。。。发现，使用。。。。可以获得更好的结果。
The disadvantage of this method, and other planar based approximations, e.g. [25], is that they can have difficulty modeling thin structures.
该方法的缺点在于。。。
In this work, we perform a comparison to the Deep3D image formation model, and show that our algorithm produces superior results.
本文中，我们与。。进行了对比，并证明我们的算法能获得更好的结果。
```

## Method
```
Our framework relies on the user providing an initial estimate of the depth, where the user marks objects and regions as closer or farther from the camera.
我们的框架依赖于。。。
To ensure the highest level of flexibility, we treat both images and video the same—as -connected graphs.
为了保证。。。，我们。。。。
In addition, we propose a refinement scheme to improve depth map accuracy by incorporating spatial smoothness.
此外，我们提供一种改进方案。。。
Instead, we propose a solution based on optical flow which solves for a dense correction field.
相反，我们提出了一种。。的方案。
One challenge is that defocus alters the appearance of each frame differently depending on the focus settings.
一个挑战在于。。。
We overcome this problem by concatenating flows between consecutive frames in the focal stack, which ensures that defocus between two input frames to the optical flow appear similar.
我们通过。。。来解决这个问题。
In our framework, for the sake of memory constraints, this is a 6-connected graph: a frame is connected in a 4-way fashion, in addition to the node in the same spatial location in the previous frame, as well the next frame.
在我们的框架中，为了保证。。。
The practical reasons of combining these two methods will become evident later, but we first discuss how we generate the depth maps for each framework separately.
。。。的实际原因是。。。我们首先讨论。。。
For the purpose of image segmentation, the goal is to classify every pixel in an image to belong to one of possible labels.
为了。。。的目的，目标是。。。
This is performed by solving a linear system of equations
这是通过。。。而执行的。
For use in generating depth maps, we modify this methodology in the following way.
为了。。。，我们以以下方式修改此方法。
The goal is to solve...
目标是为了。。。
As such... 
Therefore...
因此。。。
In some cases, even this will not always result in every pixel being classified, but region filling methods can be used to correct this.
在某些情况下，即使。。。但是。。。
For the data costs, we use a modified Potts model, rather than the negative log histogram probability as done in [15]. The reason why was due to the nature of the color space to represent images.
我们使用。。。，而不是。。。原因在于。。。。
It should be noted that there are some portions of the image that failed to be assigned any labels, such as the area around the right of the garbage can.
应该注意的是。。。
After Graph Cuts has completed, this correspondence is used to map back to the continuous range.
。。。做完后，。。。
The reason is because the edge weights from Random Walks ultimately considered the depth prior as only one component of information out of the overall feature vector used.
原因在于。。。
Before explaining the mechanics of how video conversion is performed, we are assuming that there are no abrupt changes in the video being processed, or consisting of a single camera shot.
为了解释。。。的机制，我们假设。。。
As mentioned earlier in Section I,
正如在第。。节提到的。。。
This overall process inevitably creates....
整个过程不可避免的造成了。。。。
Essentially
实质上。。。
We thus modify the NNC framework to incorporate the similarity between two color patches using Phan et al.’s framework.
因此，我们修改了。。。来。。。
Further details on how these descriptors were computed, and how they are adapted into the TLD framework can be found in [26].
更多详细的细节，关于。。。，可以参考。。。
Further details regarding the overall process of achieving temporally consistent optical flow can be found in [30].
更多的关于。。。的细节可以参考。。。
This will function well when different parts of the object appear at different depths
当。。。情况时，这将很好的运行
Noting this drawback, we offer an alternative method that the user may choose.
注意到这个缺点，我们提供。。。。
The framework that we use is the based on the one by Tao et al.
我们使用的框架是基于。。。。
We can thus improve accuracy by using the frames in the video sequence as guidance images.
因此，通过使用。。可以提高。。。
To address this, one complete iteration consists of a 2D filtering operation, with the addition of a temporal filtering operation.
为了解决这个问题。。。
To determine these, one simply needs to take the every spatial co-ordinate in the one frame, and use the vectors to determine where these pixel locations are best located in the next frame.
为了确定这些。。。
To solve this problem, we propose a technique to detect bokeh regions by looking for bright areas and measure each pixel’s expansion through the focal stack.
为了解决这个问题。。。
To fix this, we incorporate the bokeh detector into a modified data term E of the previous MRF formulation as follows:
为了解决这个。。。我们加入了。。。
By doing this, we can determine a binary map for each frame
通过这样做，我们可以。。。。
Specifically,
特别地。。。
To further increase accuracy, we introduce an occlusion term, so that those locations that are likely to be occluded do not contribute substantially to the output.
为了进一步提高准确率。。。
We assume that the scene is Lambertian and is captured by a camera following a thin-lens model.
我们假设。。。
This assumption allows us to evaluate the rendered result of each pixel by a simple convolution.
这个假设可以让我们。。。
Given the assumption that blur is locally shift-invariant, we can generate a blur stack...
基于。。。的假设，我们可以。。。
In practice, we generate a stack with blur radius increasing by 0.25 pixels between consecutive frames.
实践中，我们。。。。
This non-linear least squares problem can be solved using Levenberg-Marquardt.
这种。。问题可以通过。。。来解决。
In our implementation, we use Ceres Solver [1] with sparse normal cholesky as the linear solver.
在我们的实现中，我们使用。。。来。。。
Following the approach of []
根据文献。。。。
The proposed pipeline consists of two major stages.
我们的方法流程包括两个主要部分。。
The key assumption in the second stage is that the scene consists of objects that are connected in space.
第二步中主要的假设在于。。。
In particular, we assume that dynamic objects are connected to the surrounding environment.
特别的，我们假设。。。
This assumption is true for many scenes likely to be encountered by a mobile vision system, such as a robot or a wearable device.
很多场景下这种假设是成立的。。。。
To measure the fitting error of the motion models with re spect to the observed correspondences, we compute the....
为了衡量。。。，我们计算。。。。
Let us first consider a simplified example, where the number of independent motions is known a priori.
让我们先看一个简单的例子。。。。
These subproblems can be approximately solved using a reweighted version of the normalized 8-point algorithm.
这个子问题可以用。。。算法近似解决。。。。
We again perform alternating minimization based on this new label set and repeat this process until no further decrease in energy can be made.
我们执行。。。基于。。。
A summary of the algorithm can be found in Algorithm 1.
该算法的一个总结可以看。。。。
To resolve scale ambiguities and assemble the scene, we use a prior assumption that is often appropriate in daily life.
为了解决。。问题，我们使用。。。
We model this assumption using a combination of two constraints:
我们使用两个约束的组合来建模这个假设...
we formulate these constraints as an energy minimization problem defined on a superpixel graph.
我们将这些约束作为....问题来制定。
Instead of trying to directly predict the depth, we instead attempt to find the correspondence field d r that when applied to the left image would enable us to reconstruct the right image,
与。。相对的。。，我们并不。。。而是试着发现。。。
To produce more robust results, we train our network to predict both the left and right image disparities
为了获得更鲁棒性的结果。。。。
Our network architecture is outlined in Table 1 and consists of 31 million parameters that we learn.
我们的网络模型如表。。所示，包含。。。个参数。。。
It is important to note that...
需要重点注意的是。。。。
```

## Formula
```
If we let represent the depth from the depth prior at pixel
我们令。。。表示。。。
the edge weight equation is modified by modifying the Euclidean distance, which is defined as:
。。。的公式按照。。来修改，可以被定义为。。。
a is a positive real constant, which we set to 0.5, serving as a scaling factor determining how much contribution the depth prior has to the output.
。。。我们设置为。。。表示。。。。
y denotes the depth at pixel from the depth prior.
。。表示。。。
These were experimentally set to...
这些值被实验性的设置为。。。
Additionally, let us define the vector x, of size, where the th row is the probability that the pixel will be assigned a particular label, . By letting represent the user-defined label of the th pixel, for a particular user-defined label , vector is defined as:。。。
另外，我们定义。。。，那么。。可以被定义为。。。
we thus obtain the following decomposition for y:
我们因此得到。。。
Finally, to solve for the unknown probabilities for the label , we solve the matrix equation of xx
最后，为了解决。。。我们求解。。。
After this step, we can produce an aligned frame
这步之后，我们可以获得。。。
Let M be the number of pixels in the image.
M表示。。。
Specifically, we will make use of the following norm:
特别的，我们使用如下的归一化方法。。。
We denote the standard Euclidean norm by ·....and use subscripts whenever a different norm is used.
我们使用。。。来表示。。。
We formulate this as a joint labeling and estimation problem,
我们将。。。看作是一个。。。问题
The parameter λ > 0 controls the overall smoothness of the solution
参数。。。用来控制。。。。
```

## Figure
```
Fig. 5 illustrates a sample shot, with their labels overlaid, showing what happens when only...
图。。展示了。。。
We show an example of this in Fig. 4, which is a snapshot of an area on the Ryerson University campus.
我们在图。。中显示了一个例子，是。。。的一个。。
A flow chart illustrating our framework is seen in Fig. 2.
图。。显示了我们的框架流程图。
For the sake of brevity...we only show the labels for frames 1, 19 and 38.
为了简洁起见。。。我们仅仅。。。
As can be seen,...
可以看到。。。
We illustrate our loss module in Fig. 2.
图。。描述了我们的。。。
From Fig. 3 we can see that Deep3D produces plausible image reconstructions but the output disparities are inferior to ours.
通过图。。我们可以发现。。。。
```

## Experiment
```
To demonstrate the full effect of labelling with different intensities or different colors, the figures vary in their style of labelling
为了展示。。。
The images of Fig. 8 have also been chosen on purpose, as there are prominent objects in the foreground, while there are other elements that belong to the background.
图。。也是被选择的，主要是为了说明。。。
To provide a benchmark with our work, we also compare with our own implementation of Guttmann et al.’s framework.
为了提供我们工作的基准，我们还将与我们自己实施的。。。。等人的框架进行比较。
In order to be consistent, the depth map for the last frame
为了保持一致性。。。。
The result of the system generates a set of depth maps—one per frame—to be used for rendering in stereoscopic hardware.
系统的结果。。。。
We begin our results by using a test set available on the Middlebury Optical Flow database
我们使用。。数据集来展示我们的成果。
As can be seen, the depth map that Guttmann et al.’s framework generated does not agree perceptually in comparison to the proposed framework.
可以看到，。。。。
Our framework not only respects object edges, but allows some internal variation within the objects to minimize the cardboard cutout effect.
我们的系统不仅可以。。。。而且可以。。。
These experiments were all performed on an Intel Quad 2 Core Q6600 2.4 GHz system, with 8 GB of RAM.
我们的实验基于。。。的硬件环境。
Table II shows these subjective results. As seen, an overwhelming majority of students preferred our method
表。。显示了。。。结果，可以看到。。。。
This is understandable, as it is common for viewers of stereoscopic content to experience visual discomfort with high amounts of motion, as the isparities can widely change throughout the shot.
。。。。这是可以理解的，因为。。。
We evaluate runtime on the “balls” dataset (Figure 7) with 25 frames at 640x360 pixels on a single CPU core of Intel i7-4770@3.40 Ghz.
我们在。。数据集上来进行实时测试，环境为。。。
We demonstrate our aligned focal stack results in the supplementary video and through a comparison of all-in-focus photos generated by our method, Adobe Photoshop CS5, and HeliconFocus in Figure
我们通过比较。。来展示我们的结果。。
However, our method is able to produce an all-in-focus that does not suffer from Bokeh bleeding,
我们的方法可以。。。。
We also compare depth maps from our algorithm to a representative of previous work by replacing optical flow alignment with affine alignment
我们还将我们的方法和。。。做了对比。。。。
Results show that...
结果表明。。。
We evaluate the presented approach quantitatively and qualitatively on two datasets that depict complex and realistic dynamic scenes
我们使用。。。来衡量我们的结果。。。。
To the best of our knowledge, this is the first quantitative evaluation of monocular reconstruction on dynamic scenes of this complexity.
据我们所知。。。。。
The accuracy of the presented approach is compared to two state-of-the-art techniques for monocular depth estimation from video.
本方法的准确性与两个最新的技术相比较。。。
the second approach we compare to is the nongigid structure-from-motion formulation of Fragkiadaki et。。。
第二个比较的方法是。。。。
Accuracy is reported using three standard measures.
准确性采用三种标准方式来衡量。。。
For completeness, we also report the root mean square error
为了完整性，我们还使用了。。。。
The dataset provides sparse ground-truth depth measurements acquired by a LiDAR scanner.
该数据集提供了。。。
We compared the presented approach to the prior approaches introduced above.
我们将本方法与前面提到的方法进行了比较。。。
We thus report results for depth transfer (DT)
我们报告了。。。的结果。
Our approach achieves a higher accuracy than DT on all reported metrics, without relying on any training data.
我们的方法获得了。。。。
The results demonstrate that the presented approach substantially outperforms the prior work with any of these input flows.
结果表明。。。。
the presented approach reduces the MRE by 40% relative to DT [19] and by 30% relative to NR-SfM.
本方法相比。。。降低了。。。。
A qualitative comparison is shown in Figure 5.
定性比较如图。。
An example result from our algorithm is illustrated in Fig. 1.
一个应用我们算法的结果如图。。。
Here we compare the performance of our approach to both supervised and unsupervised single view depth estimation methods.
我们将本文算法和。。。。进行比较。
To evaluate our image formation model, we compare to a variant of our model that uses the Deep3D [9] image formation model,
为了衡量我们的模型，我们和。。。进行了比较。。
The network is implemented5 in Torch [42] and takes on the order of 20 hours to train using 2 NVIDIA GeForce GTX TITAN X GPUs on a dataset of 30 thousand images for 50 epochs. Inference is fast and takes less than 50 ms (or more than 20 frames per second) for an 768 × 256 image, including transfer times to and from the GPU.
网络的训练条件如下。。。。
During optimization, we set the weighting of the different loss components to α ap = 1 and α lr = 1 .
训练时使用的参数。。。。
Data augmentation was performed on the fly and it included horizontally flipping the input images and then swapping the left and right images so they were still in the correct position relative to each other.
数据增强。。。。
We present results for the KITTI dataset [47] using two different test splits, to enable comparison to existing works.
我们使用。。。对我们的算法进行测试，和其他已有算法进行对比。。。。
We evaluate on the 200 high quality disparity images provided as part of the official KITTI training set.
我们在。。上进行衡量。。。
Quantitative results are presented in Table 3 with some example outputs shown in Fig. 6.
主观结果。。。
Even though our left-right consistency check improves the quality of the results, there are still some artifacts visible at occlusion boundaries due to the pixels in the occlusion region not being visible in both images.   
Issues due to occlusion are also apparent at the left image border where the corresponding pixels are also typically not visible in the second view.
It may be possible to improve some of these issues by more explicitly reasoning about occlusion during training
尽管。。。。仍然。。。。（对结果的分析）， 问题在于。。。。。可能的解决方案是。。。。
```

## Conclusion
```
We presented a semi-automatic system for obtaining depth maps for unconstrained images and video sequences, for the purpose of stereoscopic 3D conversion.
我们提出了。。。，目的是。。。
The core of our system incorporates two existing semi-automatic image segmentation algorithms in a novel way to produce stereoscopic image pairs.
我们系统的核心在于。。。
For future research, we are currently investigating how to properly set this constant, as it is currently static and selected a priori.
对于未来的研究，我们正在调查。。。。
We are investigating possible means for adaptively changing based on some confidence measure to determine whether one paradigm is preferred over the other.
我们正在试验可能的手段（方法）来。。。。
One avenue of research is to use Active Frame Selection [31], where a prediction model determines the best keyframes in the video sequence for the user-defined labeling.
研究的一个途径是。。。
Another area of research is to discard object tracking completely, and rely on the optical flow method, as it can be more efficiently calculated.
研究的另一个i领域是。。。
Overall, our framework is conceptually simpler than other related approaches, and it is able to achieve better results.
总体来说，我们的方法。。。。
Our approach has been demonstrated on a range of challenging cases and produces high quality results.
我们的方法被。。。所证实。。
We presented an approach to dense depth estimation from monocular video.
我们提出了一个。。。方法。。
An important direction for future work is the incorporation of additional prior knowledge into our geometric framework.
为了一个主要的研究方向是。。。。
Other opportunities for future work are to couple the optical flow estimation and multiple model fitting and to enforce temporal consistency.
未来其他可能的的方向是。。。。
In future work, we would like to extend our model to videos.
未来的工作。。。。
It would also be interesting to investigate sparse input as an alternative training signal
对。。进行进一步研究也是有意义的 。。
```


## To ADD
```
Introduction
Even though RD optimization is not mandatory for standard video compression such as H.264 [3], it is a main part of video coding to improve coding efficiency. However, there were only few papers that analyzed the Lagrange multiplier itself.
As a consequence, it has been noted that when a sequence is encoded at low bit-rate, a large share of resources is allocated to MVs.
To achieve this target we propose the lossy coding of MVs, obtained thanks to scalar quantization.

In order to reduce the cost of the motion information, XXX et. al .[] presented ...

The main difference between the proposed solution and those that can be found in the scientific literature is that ...
Unlike previous approaches, ...

The rest of this paper is organized as follows.
Experimental results are shown in Section V. Section VI concludes this paper.
Main Body
From the results of the previous work, ....
Thus, ...
Therefore, ...
Consequently, ...
Furthermore, ...
Moreover, ...
Next, ...
On the contrary, ...
Based on this observation,  ...
In order to experimentally estimate ...
It will be confirmed in Section V.
From these observations, ...
These statistics suggest that,...
... because of the following three reasons. ...
To our knowledge, ...
(at the authors’ best knowledge)
The new coding mode works as follows: first, ...
Figure and Table
... as denoted in Fig. 1.
Fig. 1 illustrates that ...
Table 1 lists ....
It can be confirmed from Fig. 1 that ...
Table 3 shows very interesting results, i.e., ...
It implies that ...
Experiment
We apply the proposed ... to the JM reference model.
In order to quantify relative efficiency of between(of)...
We evaluate the proposed method to various sequences including low to high motion sequences and different resolutions from quarter common intermediate format (QCIF) to high definition (HD) sequences.
Here, we show experimental results of the proposed methods with ...
Experimental results are listed in Table V and VI.
Finally, we observe that ...
To demonstrate the difference between the methods parts of the images have been magnified at 1024×768 pixels resolution

Conclusion
It also showed that ...
We considered ... in the future work.
```