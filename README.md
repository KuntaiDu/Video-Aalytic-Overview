# Video analytic overview

## Introduction

Deep learning models are amazingly successfull in analyzing videos. 
Correspondingly, more and more videos are generated and waiting for being analyzed.
However, deep learning models are REALLY compute intensive, and videos are really huge in terms of size. 
Thus, to support video analytic workload, the key research topic is how to reduce computation and 

Knowing that 

## Video analytic pipelines

### Image-based


#### Glimpse

#### Edge Assisted Real-time Object Detection for Mobile Augmented Reality
Here is the [paper link](http://www.winlab.rutgers.edu/~luyang/papers/mobicom19_augmented_reality.pdf). 
This paper explores AR scenario. 
The key thing is to minimize the latency.
This paper use parallel streaming and inference to reduce latency, motion-vector-based tracking & ROI encoding to reduce bandwidth (thus reduce streaming latency), and adaptive offloading to reduce compute cost.

### Video-clip-based

### AWStream

## Scale up inference

### Through building effective library

The key research topic here is how to choose correct API set and provide clever implementation to save unnecessary cost.

#### Starfish
Here is the [paper link](http://roblkw.com/likamwa2015starfish-mobisys.pdf).
This paper argues that multiple applications will reuse the same video and invoke the same library. So one could cache the result for future use.


#### Scanner

Here is the [paper link](http://graphics.stanford.edu/papers/scanner/poms18_scanner.pdf).
It expresses the analytic pipeline as a static computation graph, bound the temporal dependency through pre-defined API, and scale the pipeline to a cluster.

### Through building database

#### DeepLens
Here is the [paper link](http://cidrdb.org/cidr2019/papers/p40-krishnan-cidr19.pdf).
This paper says that each step of video analytic pipeline will map from a stream to another stream.
Based on this abstraction, they explore how to encode, index the vido; and how to reuse previous results.

#### NoScope
Here is the [paper link](https://www.vldb.org/pvldb/vol10/p1586-kang.pdf).
This paper targets object detection. It says that by biasing the model to current video and specific classes, the model could be much more cheaper.

#### Focus
Here is the [paper link](https://www.usenix.org/system/files/osdi18-hsieh.pdf).
This paper tries to detect all frames that contains certain objects. They use cheap models to reduce ingest-time cost, and identify same/similiar objects to reduce query-time latency.

### Through resource management

#### MCDNN
Here is the [paper link](https://homes.cs.washington.edu/~arvind/papers/mcdnn.pdf).

## Scale up training

### Mainstream
Here is the [paper link](https://www.usenix.org/system/files/conference/atc18/atc18-jiang.pdf).
This paper argues that people train multiple models based on same backbone on same videos.
Thus, the backbone could be shared between different models.

## Benchmark video analytic pipelines

## Benchmark video analytic databases

### Visual Road
Here is the [paper link](https://db.cs.washington.edu/projects/visualroad/p300-haynes.pdf).
This paper argues that to benchmark video analytic databases, the generation of benchmark videos and the the annotate of those videos should be automatic.
So they use synthetic way to generate videos.

