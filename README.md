# Instructions of running parboil benchmark using GPGPU-Sim 4.0

## Step1: Add path to the ~/.bashrc file

Since I use CUDA-10.1 and it was installed in /usr/local/cuda-10.1,  the following line was added to the ~/.bashrc file:

export CUDA_PATH=/usr/local/cuda-10.1
 
export CUDA_INSTALL_PATH=/usr/local/cuda-10.1

export PATH=$PATH:/usr/local/cuda-10.1/bin

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-10.1/lib:/usr/local/cuda-10.1/lib64

## Step2: Build the GPGPU-Sim 4.0 
(1) Clone the GPGPU-Sim 4.0 

    git clone https://github.com/gpgpu-sim/gpgpu-sim_distribution.git

(2) Then type:

    cd gpgpu-sim_distribution
    
    make clean
    
    make
## Step3: Run parboil benchmarks

(1) Clone the parboil benchmark:

    git clone https://github.com/peiyi1/parboil_benchmark.git
    
(2) Switch to branch v1:

    git checkout v1
    
(3) File Makefile.conf was created in /parboil/common/ to add the following paths. You can change the paths if you use different paths.

    CUDA_PATH=/usr/local/cuda-10.1
    
    CUDA_LIB_PATH=/usr/local/cuda-10.1/lib64
    
    CUDAHOME=/usr/local/cuda-10.1
    
(4) Suppose you want to compile the CUDA version of the benchmark "bfs".  Then go to /parboil/ and type the following command:

    ./parboil compile bfs cuda
    
(5) File compile_all_benchmarks was created to compile the CUDA version of all the benchmarks, and you can type the following command to compile:
    
    ./compile_all_benchmarks
    
(6) Folder named "experiments" was created to run the CUDA version of all the benchmark, and configuration files in the folder of gpgpu-sim_distribution/configs/tested-cfgs/SM7_QV100 were used to run the simulation. Supporse you want to run the "bfs" benchmark, then go to /parboil/experiments/bfs and modify the file named "run". In the file named "run", you need to change the path of "/home/pli11/Videos/parboil_new_simulator/" to your own paths, and you can change the datasets by changing the path after the "-i" flag. After the modification of this "run" file, we can run benchmarks by typing:

    ./run

