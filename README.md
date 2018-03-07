# Tensors_et_al.
Geomatics_n_ComputerVision_with_Tensorflow



![alt text](../master/tensor_pic.png "Tensor")
#


### Tensor ==

Wiki - In mathematics, tensors are geometric objects that describe linear relations between geometric vectors, scalars, and other tensors. Elementary examples of such relations include the dot product, the cross product, and linear maps. Geometric vectors, often used in physics and engineering applications, and scalars themselves are also tensors.

https://en.wikipedia.org/wiki/Tensor

#

### Main Source ==
https://github.com/chiphuyen/stanford-tensorflow-tutorials

#
#### TIME STAMP -7th-MAR-18 --- 1100h 
### Installation Errors == 
Initial hiccups ...
#
```python
(tensor) dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a1_18/a1____Tensor_Mar18/Tensor$ 
(tensor) dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a1_18/a1____Tensor_Mar18/Tensor$ python
Python 3.6.2 |Continuum Analytics, Inc.| (default, Jul 20 2017, 13:51:32) 
[GCC 4.4.7 20120313 (Red Hat 4.4.7-1)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
>>> import tensorflow as tf
Illegal instruction (core dumped)
```
#
https://www.tensorflow.org/install/install_linux#installing_with_native_pip
#### pip install tensorflow
#
####PIP and PIP3 are SAME within a Conda VENV - 
- GIT Source === https://github.com/ContinuumIO/anaconda-issues/issues/1429
- SO Source === https://stackoverflow.com/questions/44362214/install-pip3-for-conda

#
#### TIME STAMP -7th-MAR-18 --- 1100h 
#### Probable solutions ...

- https://github.com/tensorflow/tensorflow/issues/8976
- https://github.com/tensorflow/tensorflow/issues/17441
- https://stackoverflow.com/questions/49081353/python-giving-illegal-instructioncore-dumped-error-when-importing-tensorflow


#
#### TIME STAMP -7th-MAR-18 --- 1100h 
#### from URL --- 
CPU only:
sudo pip3 install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.6.0-cp36-cp36m-linux_x86_64.whl
#### Error -- "not a supported wheel on this platform."
tensorflow-1.6.0-cp36-cp36m-linux_x86_64.whl is not a supported wheel on this platform.
#

#### Check Pythoon installed -- 64 BIT 0r 32 BIT

```python
(tensor) dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a1_18/a1____Tensor_Mar18/Tensor$ python
Python 3.6.2 |Continuum Analytics, Inc.| (default, Jul 20 2017, 13:51:32) 
[GCC 4.4.7 20120313 (Red Hat 4.4.7-1)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
>>> import struct;print(struct.calcsize("P") * 8)
64
>>> 
``` 
#
####  GREP Usage :- 
https://askubuntu.com/questions/55325/how-to-use-grep-command-to-find-text-including-subdirectories
#

```python
>>> 
(tensor) dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a1_18/a1____Tensor_Mar18/Tensor$ gcc -march=native -Q --help=target | grep enabled
  -m64                        		[enabled]
  -m80387                     		[enabled]
  -m96bit-long-double         		[enabled]
  -malign-stringops           		[enabled]
  -mcx16                      		[enabled]
  -mfancy-math-387            		[enabled]
  -mfentry                    		[enabled]
  -mfp-ret-in-387             		[enabled]
  -mfxsr                      		[enabled]
  -mglibc                     		[enabled]
  -mhard-float                		[enabled]
  -mieee-fp                   		[enabled]
  -mlong-double-80            		[enabled]
  -mmmx                       		[enabled]
  -mpopcnt                    		[enabled]
  -mpush-args                 		[enabled]
  -mred-zone                  		[enabled]
  -msahf                      		[enabled]
  -msse                       		[enabled]
  -msse2                      		[enabled]
  -msse3                      		[enabled]
  -msse4                      		[enabled]
  -msse4.1                    		[enabled]
  -msse4.2                    		[enabled]
  -mssse3                     		[enabled]
  -mstackrealign              		[enabled]
  -mtls-direct-seg-refs       		[enabled]
(tensor) dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a1_18/a1____Tensor_Mar18/Tensor$ 

```
#



