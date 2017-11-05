# Texture Synthesis
## Introduction
For this tutorial we will be using [Xavier Snelgrove](https://twitter.com/wxswxs)’s [subjective-functions](https://github.com/wxs/subjective-functions) repository. You can also read his research paper [High-Resolution Multi-Scale Neural Texture Synthesis](http://wxs.ca/research/multiscale-neural-synthesis/) to learn more about how it works.

## Source Materials
Texture-rich photographs / image files (512x512 min). Examples would be, wood grain on a table, a rug with a geometric pattern, or a graffiti covered wall.
[Wikimedia Commons](https://commons.wikimedia.org/wiki/Main_Page)

## Set Up
1. Get the repository.
```
$ cd ~/path/to/Projects/	 # project directory
$ git clone https://github.com/wxs/subjective-functions.git
```

2. Install the project requirements
```
$ cd subjective-functions
$ pip3 install -r requirements.txt
```

3. Run locally
This will likely be very slow as it runs on your GPU.
```
$ KERAS_BACKEND=tensorflow python3 synthesize.py -s bark.jpg
```

In Finder navigate to `subjective-functions/output`. You will see images slowly being generated. The first image is the “seed” of noise (for randomization) and will most likely just look black. The final ones should look similar, in texture, to the source image (`bark.jpg` in this instance).

You can see how slowly they are being generated, so lets speed this up (and free up your system) by using some cloud GPUs.  `control + c`

4. Initialize your FloydHub Project
```
$ cd ~/path/to/subjective-functions
$ floyd init subjective-functions
```

This will initialize a project for you in your [FloydHub account](https://www.floydhub.com/projects).

5. Run Subjective Functions on FloydHub
```
$ floyd run --gpu "python3 synthesize.py -s bark.jpg --data-dir /vgg_weights --output-dir /output" --data wxswxs/vgg-weights/1:vgg_weights
```

It should sync the code with the server and give you a job id.
```
JOB NAME
-----------------------------------------
brendann/projects/subjective-functions/39
```

6. View the output images.
	1. Navigate to https://www.floydhub.com/jobs and you should see your job running.
	2. Click on the job (in my case it is 39) and you should see the log.
	3. Click the “Output” tab at the top then click the specified output folder. You should see the generated images.
	4. Refresh the page and you will see that more and more images are created.
*The gui doesn’t update that well so you may need to hard refresh the page every now and then.

## Read More
* [High-Resolution Multi-Scale Neural Texture Synthesis](http://wxs.ca/research/multiscale-neural-synthesis/)
* [Neural Algorithm of Artistic Style](https://arxiv.org/abs/1508.06576)

