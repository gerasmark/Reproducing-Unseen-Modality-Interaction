# Reproducing-Unseen-Modality-Interaction-Results-for-the-MSR-VTT-Dataset
In this work, we analyze and try to reproduce the results of Yunhua Zhang, Hazel Doughty, Cees G.M. Snoek Learning Unseen Modality Interaction In NeurIPS, 2023.

## Reproducibility Summary

### Scope of Reproducibility
In this work, we analyze and try to reproduce the results of ”Learning Unseen
Modality Interaction”. We focus on reproducing the results for the multime-
dia retrieval task, using the MSR-VTT dataset. We attempt to see if these
results can easily be replicated by following their methodology and trying to
learn from modality-incomplete training data.

### Methodology

We use the implementation of the model released by the authors for their paper.
However, the code released by the authors is incomplete and not able to run at
all. In addition, it only refers to one of the three datasets used in the paper
(EPIC-KITCHENS), making the reproduction more difficult. The code is also
missing important parts for the retrieval task such as the environments and
dependencies used, the evaluation metrics and ablations studied in the paper.
Therefore, we had to we extend the code by following the details in the paper
and adding the missing parts to fit the MSR-VTT dataset, which contains five
more modalities than the EPIC-KITCHENS dataset, requires a different data
loader, different evaluation metrics and tweaks in the model architecture and
loss function. We also found out that the model architecture was missing one
layer specified in the paper that we had to add.
We conducted our experiments on an NVIDIA P100 GPU, requiring less
than half an hour of training.

### Results

The code released by the authors could not be run on the MSR-VTT dataset, so
the reproduction was substantially different. There were many different errors
on the code for which we had to implement our own solutions, which could differ
from what the authors did.
Our results were close to the ones mentioned in the paper, and better
than the papers the authors used for comparison. Our best implementation
managed to get state-of-the-art results, close enough to the paper’s claims, and
sometimes even better.
Therefore, we conclude that the paper is somewhat replicable but definitely
not readily reproducible, and the claims made by the authors are most likely
valid. We can only conclude this for the multimedia retrieval part of the paper,
and not the whole paper.

### What was easy

It was easy to identify the main claims of the paper and understand the rea-
soning behind the model that the authors proposed. The code that the authors
provided gave us a good idea of how to reproduce the results, although many
steps were needed. We did not have to make substantial changes to the reorga-
nization module and the alignment module of the code.

### What was difficult

Setting up the development environment was challenging because of the lack
of clear steps from the authors and a lack of a complete list of dependencies.
Having to identify issues within the code and solve them ourselves was also very
demanding, as we did not get any help from the researchers. The code having
a missing layer in the transformer also took a lot of effort to fix.
We had to study other work on the same dataset to get an idea of how to
proceed, mainly inspecting the works mentioned in the paper that are used as
comparison, before we could start recreating the code. Most of our time was
spent pinning down the dependencies and finding open source implementations
of similar papers so that we could create our custom data loaders, metrics and
loss functions.

### Communication with original authors

We communicated with the authors via email, since they had not initially up-
loaded any code for the paper. They sent us their code for the EPIC-KITCHENS
dataset, which was supposed to be the code they submitted for review, but the
code had many errors and could not be executed.
They claimed that it would be easy to reproduce the results, since the code
was supposed to be the same for all three datasets they used, and all we would
have to do it change the data loaders to load the MSR-VTT dataset. This was
far from the truth, as most of the parts needed to execute the code for the
MSR-VTT dataset were not included, and the parts that were included either
had errors, or were incomplete (like the missing fully connected layer).
The authors did not provide any further help and did not respond to any
more emails after the aforementioned claim.
