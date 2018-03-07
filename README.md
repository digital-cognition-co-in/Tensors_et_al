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
#### PIP and PIP3 are SAME within a Conda VENV - 
- GIT Source = https://github.com/ContinuumIO/anaconda-issues/issues/1429
- SO  Source = https://stackoverflow.com/questions/44362214/install-pip3-for-conda

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

#### Check Python instalation , is it - 64 BIT or 32 BIT

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


#
#### TIME STAMP -7th-MAR-18 --- 1145h 
Probable solutions - 

illegal instruction error when building Tensorflow from source
- https://stackoverflow.com/questions/45877158/illegal-instruction-error-when-building-tensorflow-from-source

- 

# 
If it were a "SEGMENTATION FAULT"  
- As suggested above - imported numpy before importing TF - same error == Illegal instruction (core dumped)
- But in my case its a - "Illegal instruction (core dumped)"


```python
(tensor) dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a1_18/a1____Tensor_Mar18/Tensor$ python
Python 3.6.2 |Continuum Analytics, Inc.| (default, Jul 20 2017, 13:51:32) 
[GCC 4.4.7 20120313 (Red Hat 4.4.7-1)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
>>> import numpy
>>> 
>>> import tensorflow
Illegal instruction (core dumped)
(tensor) dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a1_18/a1____Tensor_Mar18/Tensor$ 


```

#
http://sourceware.org/gdb/current/onlinedocs/gdb/
#

```python 
#
(tensor) dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a1_18/a1____Tensor_Mar18/Tensor$ gdb python
GNU gdb (Ubuntu 7.11.1-0ubuntu1~16.5) 7.11.1
Copyright (C) 2016 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
<http://www.gnu.org/software/gdb/documentation/>.
For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from python...done.
(gdb) 
(gdb) r
Starting program: /home/dhankar/anaconda2/envs/tensor/bin/python 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
Python 3.6.2 |Continuum Analytics, Inc.| (default, Jul 20 2017, 13:51:32) 
[GCC 4.4.7 20120313 (Red Hat 4.4.7-1)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
>>> import tensorflow
[New Thread 0x7ffff2736700 (LWP 2962)]
[New Thread 0x7ffff1f35700 (LWP 2963)]
[New Thread 0x7fffed734700 (LWP 2964)]

Thread 1 "python" received signal SIGILL, Illegal instruction.
0x00007fffe29ef880 in std::pair<std::__detail::_Node_iterator<std::pair<tensorflow::StringPiece const, std::function<bool (tensorflow::Variant*)> >, false, true>, bool> std::_Hashtable<tensorflow::StringPiece, std::pair<tensorflow::StringPiece const, std::function<bool (tensorflow::Variant*)> >, std::allocator<std::pair<tensorflow::StringPiece const, std::function<bool (tensorflow::Variant*)> > >, std::__detail::_Select1st, std::equal_to<tensorflow::StringPiece>, tensorflow::StringPieceHasher, std::__detail::_Mod_range_hashing, std::__detail::_Default_ranged_hash, std::__detail::_Prime_rehash_policy, std::__detail::_Hashtable_traits<true, false, true> >::_M_emplace<std::pair<tensorflow::StringPiece, std::function<bool (tensorflow::Variant*)> > >(std::integral_constant<bool, true>, std::pair<tensorflow::StringPiece, std::function<bool (tensorflow::Variant*)> >&&) ()
   from /home/dhankar/anaconda2/envs/tensor/lib/python3.6/site-packages/tensorflow/python/../libtensorflow_framework.so
(gdb) 
(gdb) quit
A debugging session is active.

	Inferior 1 [process 2951] will be killed.

Quit anyway? (y or n) y


```

#



