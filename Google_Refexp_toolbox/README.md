# Python toolbox for the Google Referring Expressions Dataset


The Google RefExp dataset is a collection of text descriptions of objects in 
images which builds on the publicly available [MS-COCO](http://mscoco.org/) 
dataset. Whereas the image captions in MS-COCO apply to the entire image, this 
dataset focuses on
text descriptions that allow one to uniquely identify a single object or region 
within an image.
See more details  in this paper: [Generation and Comprehension of Unambiguous Object Descriptions](http://arxiv.org/abs/1511.02283)

## Sample of the data <a name="google_refexp"></a>

Green dot is the object that is being referred to.
Sentences are generated by humans in a way that uniquely describes the
chosen object.

<table width="100%">
  <tr>
    <td  align="center"><img src="http://www.stat.ucla.edu/~junhua.mao/projects/obj_descrip_folder/sample_images/pic_001.jpg" alt="Mountain View" width="95%"></td>
    <td  align="center"><img src="http://www.stat.ucla.edu/~junhua.mao/projects/obj_descrip_folder/sample_images/pic_002.jpg" alt="Mountain View" width="95%" align="center"></td>
    <td  align="center"><img src="http://www.stat.ucla.edu/~junhua.mao/projects/obj_descrip_folder/sample_images/pic_003.jpg" alt="Mountain View" width="95%" align="center"></td>
  </tr>
  
  <tr>
    <td valign="top">
      <ul>
      <li>A girl wearing glasses and a pink shirt.</li>
      <li>An Asian girl with a pink shirt eating at the table.</li>
      </ul>
    </td>
    <td valign="top">
      <ul>
      <li>A boy brushing his hair while looking at his reflection.<br></li>
      <li>A young male child in pajamas shaking around a hairbrush in the mirror.</li>
      </ul>
    </td>
    <td valign="top">
      <ul>
      <li>Zebra looking towards the camera.<br></li>
      <li>A zebra third from the left.</li>
      </ul>
    </td>
  </tr>
</table>


## Requirements
- python 2.7 (Need numpy, scipy, matlabplot, PIL packages. All included in 
[Anaconda](https://store.continuum.io/cshop/anaconda/))

## Setup and data downloading


### Easy setup 

  ```
  cd $YOUR_PATH_TO_THIS_TOOLBOX
  python setup.py
  ```
  
Running the setup.py script will do the following five things:

1.  Download Google Refexp Data
2.  Download and compile the COCO toolbox
3.  Download COCO annotations
4.  Download COCO images
5.  Align the Google Refexp Data with COCO annotations

At each step you will be prompted by keyboard whether or not you would like to 
skip a step.
Note that the MS COCO images (13GB) and annotations (158MB) are very large and 
it takes some time to download all of them. 

### Manual downloading and setup

You can 
download the GoogleRefexp data directly from this 
[link](https://storage.googleapis.com/refexp/google_refexp_dataset_release.zip).


If you have already played with MS COCO and do not want to have two copies of 
them, you can choose to create a symbolic link from external to your COCO toolkit. E.g.:

  ```
  cd $YOUR_PATH_TO_THIS_TOOLBOX
  ln -sf $YOUR_PATH_TO_COCO_TOOLBOX ./external/coco
  ```

Please make sure the following on are on your path:

1. compiled PythonAPI at 
external/coco/PythonAPI
2. the annotation file at 
external/coco/annotations/instances_train2014.json
3. COCO images at  external/coco/images/train2014/.

You can create symbolic links if you have 
already downloaded the data and compiled the COCO toolbox.

Then run *setup.py* to download the Google Refexp data and compile this toolbox. 
You can skip steps 2, 3, 4.

## Demos

For **visualization** and **utility** functions, please see 
*google_refexp_dataset_demo.ipynb*.

For automatic and Amazon Mechanical Turk (AMT) **evaluation** of the comprehension 
and generation tasks, please see *google_refexp_eval_demo.ipynb*; The 
appropriate output format for a comprehension/generation algorithm is described 
in ./evaluation/format_comprehension_eval.md and 
./evaluation/format_generation_eval.md

We also provide two sample outputs for reference. For the comprehension task, 
we use a naive baseline which is a random shuffle of the region candidates 
(./evaluation/sample_results/sample_results_comprehension.json). For the 
generation task, we use a naive baseline which outputs the class name of an 
object (./evaluation/sample_results/sample_results_generation.json).

If you are not familiar with AMT evaluations, please see this 
[tutorial](http://docs.aws.amazon.com/AWSMechTurk/latest/RequesterUI/amt-ui.pdf)
The interface and APIs provided by this toolbox have already grouped 5 
evaluations into one HIT. In our experiment, paying 2 cents for one HIT leads to 
reasonable results.


## Citation

If you find the dataset and toolbox useful in your research, 
please consider citing:

    @inproceedings{mao2016generation,
      title={Generation and Comprehension of Unambiguous Object Descriptions},
      author={Mao, Junhua and Huang, Jonathan and Toshev, Alexander and Camburu, Oana and Yuille, Alan and Murphy, Kevin},
      booktitle={CVPR},
      year={2016}
    }
    
## License

This data is released by Google under the following license:
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
    
## Toolbox Developers

[Junhua Mao](https://www.stat.ucla.edu/~junhua.mao/) and [Oana Camburu](https://www.cs.ox.ac.uk/people/oana-maria.camburu/)