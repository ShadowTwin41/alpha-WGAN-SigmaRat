# Generation of Synthetic Rat Brain MRI scans with a 3D Enhanced Alpha-GAN


<h4>André Ferreira, Ricardo Magalhães, Sébastien Mériaux, Victor Alves
    
  <p> <li> Collaboration between Centro Algoritmi, University of Minho, Braga, Portugal and Université Paris-Saclay, CEA, CNRS, BAOBAB, NeuroSpin, 91191 Gif-sur-Yvette, France <br>
      
<blockquote>This project is the result of André Ferreira (a81350@alunos.uminho.pt), Victor Alves (valves@di.uminho.pt), Ricardo Magalhães (ricardo.lazarus@gmail.com) and Sébastien Mériaux (sebastien.meriaux@cea.fr) work, having been developed as part of André Ferreira's master thesis in Biomedical Engineering, Medical Informatics Branch from University of Minho. </blockquote>

    Official Pytorch Implementation of "Generation of Synthetic Rat Brain MRI scans with a 3D Enhanced Alpha-GAN"

---

## Abstract

Translational brain research using Magnetic Resonance Imaging (MRI) is becoming increasingly popular as animal models are an essential part of scientific studies and more ultra-high-field scanners are becoming available. Some disadvantages of MRI are the availability of MRI scanners and the time required for a full scanning session (it usually takes over 30 minutes). Privacy laws and the 3Rs ethics rule also make it difficult to create large datasets for training deep learning models. Generative Adversarial Networks (GANs) can perform data augmentation with higher quality than other techniques. In this work, the alpha-GAN architecture is used to test its ability to produce realistic 3D MRI scans of the rat brain. As far as the authors are aware, this is the first time that a GAN-based approach has been used for data augmentation in preclinical data. The generated scans are evaluated using various qualitative and quantitative metrics. A Turing test conducted by 4 experts has shown that the generated scans can trick almost any expert. The generated scans were also used to evaluate their impact on the performance of an existing deep learning model developed for segmenting the rat brain into white matter, grey matter and cerebrospinal fluid. The models were compared using the Dice score. The best results for whole brain and white matter segmentation were obtained when 174 real scans and 348 synthetic scans were used, with improvements of 0.0172 and 0.0129, respectively. Using 174 real scans and 87 synthetic scans resulted in improvements of 0.0038 and 0.0764 for grey matter and CSF segmentation, respectively. Thus, by using the proposed new normalisation layer and loss functions, it was possible to improve the realism of the generated rat MRI scans and it was shown that using the generated data improved the segmentation model more than using the conventional data augmentation.
      
---
      
## Materials and Methods
      
An MRI dataset of the Wistar rat brain from the Sigma project was used to test the ability of GANs to produce synthetic scans. A total of 210 scanning sessions were performed using a Bruker preclinical ultra-high field scanner (11.7 Tesla) and a 4x4 surface coil dedicated to the rat head. A T2-weighted Echo Planar Imaging sequence was implemented to acquire resting-state functional data, with a spatial resolution of 0.375mm x 0.375mm x 0.5mm over a matrix of 64x64x40, a TR of 2000ms, a TE of 17.5ms and 9 averages.  Figure \ref{fig2} shows slices from three different planes (i.e. coronal, sagittal and axial) of a functional MR image of the rat brain. The dataset consists of 210 scans with a resolution of 64x64x40, which have been pre-processed to avoid complex values. For more information on the rat brain sigma dataset, see Barrière et al. (2019) or Magalhães et al. (2018) \cite{Barriere2019, Magalhaes2018a}. 

In this work, a different number of scans and sources (real or synthetic) were used in some steps of the experiment. Therefore, each dataset is formally defined as  D\textsubscript{s}\textsuperscript{N} =  {(x\textsubscript{i}, y\textsubscript{i})}\textsubscript{i=1}\textsuperscript{N}, where s indicates whether the scans are synthetic (s) or real (r), x the scans, y the respective labels and N the number of scans. The original sigma dataset of rat brains is formally defined as  D\textsubscript{r}\textsuperscript{210} =  {(x\textsubscript{i}, y\textsubscript{i})}\textsubscript{i=1}\textsuperscript{210}.
