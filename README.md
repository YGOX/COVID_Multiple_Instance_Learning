##COVID Multiple Instance Learning (MIL)

Training_models:

The running verison of the code is kept in IIAT server as well under Alex' path. To prepare data, create two subfolders (1 and 0), put covid CT images in 1 and non-covid CT images in 0. 

**main.py**:
prepare xvalidation, split datasets into train, validation and testing, according to the patient ID.
generate bags of ct slices.
create a model
train and validate
save the model achieves the best validation accuracy for each fold.

**Models.py**- build MIL models (implemented different instance based pooling strategies and embedding level pooling stratigies)

Utility functions:

**custom_layers.py** - MIL attention modules and last sigmoid layer
**data_aug_op.py**- data augmentation
**data_sorting.py**- extract patient specific folders from data root path and categories them accoording to the child.xlsx (for child data only)
**data_generator.py**- generate bags
**dataset.py**- split data into several fold and retuen the lists of patient ID

Visualization tools:

**tsne.py:** projects the models' predictions for each bag on a 2D space using t-distributed stochastic neighbour embedding (t-SNE) and allows one to perform inter-subject clustering analysis.

**patient_specific_clustering.py:** yields the same output as tsne.py but this time for intra-patient slices clustering. Also prints the distribution of the attention weights.

**show_intra_emnd.py:** uses t-SNE to build a clustering map showing the actual images (not just crosses or dots). For each clustering map, a corresponding plot is created where the corresponding attention weights are plotted. On the latter plot, adaptive thresholds are used to classify the attention weights into low, medium and high buckets using distinct colours.

**one_plot.py:** creates a single high-resolution plot of all the images in a chosen test bag, along with their learned attention weights.

**vis_attention.py:** individually prints all the images in a bag along with their learned attention weights. This is very similar to one_plot.py except that images are printed individually (and with the attention weight value on the image rather than above).
