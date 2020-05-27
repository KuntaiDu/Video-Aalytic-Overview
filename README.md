# Video analytic overview

## Video analytic pipelines

#### Glimpse

#### Edge Assisted Real-time Object Detection for Mobile Augmented Reality
Here is the [paper link](http://www.winlab.rutgers.edu/~luyang/papers/mobicom19_augmented_reality.pdf). 
This paper explores AR scenario, so the key thing here to minimize the latency.
This paper uses parallel streaming and inference to reduce latency, motion-vector-based tracking & ROI encoding to reduce bandwidth (thus reduce streaming latency), and adaptive offloading to reduce compute cost.

#### AWStream
Here is the [paper link](https://awstream.github.io/paper/awstream.pdf). 
This paper tunes the parameters of encoding algorithm.
It profiles the pareto boundary of bandwidth-accuracy trade-off, and then apply this profile on afterwards frames.
**Important**: surprisingly, this baseline is actually pretty effective because the video encoding algorithms is pretty matured in terms of preserving every details while saving bandwidth.

#### CloudSeg
Here is the [paper link](https://www.usenix.org/system/files/hotcloud19-paper-wang.pdf).
This paper uses super resolution to save bandwidth.
It trains a super resolution model based on some ground truth by minimizing analytic error, and then uses this model to super-resolute the input video clip for analytic purpose.

#### NoScope
Here is the [paper link](https://www.vldb.org/pvldb/vol10/p1586-kang.pdf).
This paper targets object detection. It says that by biasing the model to current video and specific classes, the model could be much more cheaper.

## Scale up inference

### Through building effective library/database

The key research topic here is how to choose correct API set and provide clever implementation to save unnecessary cost.

#### Starfish
Here is the [paper link](http://roblkw.com/likamwa2015starfish-mobisys.pdf).
This paper argues that multiple applications will reuse the same video and invoke the same library. So one could cache the result for future use.

#### Scanner

Here is the [paper link](http://graphics.stanford.edu/papers/scanner/poms18_scanner.pdf).
It expresses the analytic pipeline as a static computation graph, bound the temporal dependency through pre-defined API, and scale the pipeline to a cluster.

#### DeepLens
Here is the [paper link](http://cidrdb.org/cidr2019/papers/p40-krishnan-cidr19.pdf).
This paper says that each step of video analytic pipeline will map from a stream to another stream.
Based on this abstraction, they explore how to encode, index the vido; and how to reuse previous results.

#### Optasia
Here is the [paper link](https://dl.acm.org/doi/pdf/10.1145/2987550.2987564). 
This paper aims to support and optimize relational queries.
It tears specific video analytic task to four parts: extractors, processors, reducers and combiners, and then conduct optimization based on it.

#### Focus
Here is the [paper link](https://www.usenix.org/system/files/osdi18-hsieh.pdf).
This paper tries to detect all frames that contains certain objects. They use cheap models to reduce ingest-time cost, and identify same/similiar objects to reduce query-time latency.

### Through resource management

#### MCDNN
Here is the [paper link](https://homes.cs.washington.edu/~arvind/papers/mcdnn.pdf).

### Through edge


## Scale up training

#### Mainstream
Here is the [paper link](https://www.usenix.org/system/files/conference/atc18/atc18-jiang.pdf).
This paper argues that people train multiple models based on same backbone on same videos.
Thus, the backbone could be shared between different models.

## Dataset and benchmarking

#### Visual Road
Here is the [paper link](https://db.cs.washington.edu/projects/visualroad/p300-haynes.pdf).
This paper argues that to benchmark video analytic databases, the generation of benchmark videos and the the annotate of those videos should be automatic.
So they use synthetic way to generate videos.

