# Cours Vision Temps-reel

- open cv C++

## Intro
### Pourquoi la Vision temps reel?
- Acquisition, traitement et restitution en 40 ms
- Dedie aux applications de tous les jours
- Permet de tester rapidement un algo

### Quelles applications?
- Identification d'objets
- Machine learning
- Segementation et reconnaissance d'objets
- Stereovision : Vision 3D
- SFM (1 seule cam qui en bougeant peut donner une vision 3D)
- Suvi de mouvement
- Realite augmentee

### Comment les developper?
- Bibliotheque de fonctions concues pour le temps reel
- Ex OpenCV

### OpenCV
- Cree en 99 par Intel maintenue par WillowGarage
- Cross-platform
- C puis C++
- Dispo pour Java, Python, Matlab ...
- Aussi disponible pour les GPU (Cuda, OpenCL)

## Modules
- core : Structures de donnees de base
- imgproc : module de traitement d'images
- video : module d'analyse video
- calib3d : traitement image 3d
- features2d : traitement des textures 2d (id d'objets)
- objdetect : detection d'objets selon des classes predefinies
- gpu : algos d'acceleration graphique
- FLANN : matching, stiching

## Structures de base
- Headers des libs doivent etre inclus
- Classes OpenCV utilisent le namespace cv
- cv::waitKey(-1); Permet l'affichage de l'image

### Classe Mat
- bit_depth : taille d'encodage
- USF : Unsigned, Signed, Float
- number_of_channels : 1-512

### Classe point
- 2d ou 3d
- int, float ou double
- ex Point2f, Point3i, ...

### Classe Vec
- Template pour vecteurs numeriques courts
- Taille de 2 a 6 elements

### Lecture d'images
- imread
- retourne un obj de type Mat
- Flags
  - ANYDEPTH/-1 : chargement sans modif
  - COLOR/+1 : Conversion forcee en image couleur
  - GRAYSCALE/0 : Conversion en niv de gris

### Affichage d'images
- imshow (String nomDeFenete, Mat image)

## Fonctions avancees
### Image Processing (imgproc)
- **filter2D** : Filtrage lineaire, elimine le bruit
- **GaussianBlur, bilateralFilter, medianBlur** : Filtres non lineaires, reduisent le bruit en preservant la qualite de l'image
- **dilate** : convolution de l'image avec un element structurant(cercle, carre), accentue les details de l'image
- **erode** : Elimine les details
- **threshold** : Conversion en image binaire
- **Sobel** : Detection de contours (gradient)
- **Laplacian** : detection de contours (derivee seconde)
- **Canny** : detection de contours (filtre par hysteresis)
- **matchTemplate** : Trouve la position d'une partie de l'image dans l'image
- **findContours** : trouve des formes geometriques fermees
- **convexHull** : donne la forme convexe la plus petite possible qui englobe tous les points

### 2D Features
- **cornerHarris, goodFeaturesToTrack** : Detection de coins
- **orb,brisk,freak,surf,sift** : Approches pour decrire un point d'interet
- **DescriptorMatcher, BFMatcher, FlannBasedMatcher** : Permet de trouver des points correspondants dans deux images contenant les memes elements en comparant les vecteurs des points
- **findHomography, warpPerspective** : permet de determiner la transformation entre deux plans
- **CascadeClassifier** : Detecte des elements preclassifies

### Machine learning (ml)
- **CvSVM{train(),predict()}** : SVM (Support vector machine) modele d'apprentissage pour separer donnees lineaires et non lineaires
- **CvANN_MLP{create(),train(),predict()}** : Reseau de neurones (Perceptron multi-couches), processus supervise  
- **CvKNearest{train(),find_nearest()}** : comparaison de vecteurs (capable de classification non lineaire)
- **CvNormalBayesClassifier{train(),predict()}** : estime vecteurs moyens et matrices de covariance

### Calibration de camera
- **calibrateCamera**
- **solvePnP** : Estimation de la pose
- **stereoCalibrate** : determine la transformation pour passer d'une camera a l'autre
- **triangulatePoints** : reconstruit des points 3d avec des images stereo

### Video Analysis
- **calcOpticalFlowPyrLK, calcOpticalFlowFarneback** : calcule le mouvement de points d'interet
- **KalmanFilter{init(), predict(),correct()}** : tracking, estimation de position d'objets
- **calcBackProject, CamShift** : tracking base sur la couleur

### Graphical user interface (highGUI)
- Fonctions permettant de creer des interfaces graphiques
- **VideoWriter** : Permet d'enregistrer une video

## Applications
- Identification de logos basee sur les points d'interet
- Identification d'images dans une base de donnees scalable
- Realite augmentee
