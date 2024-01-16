
openMVG安装：

1.安装所需的外部库。

$ sudo apt-get install libpng-dev libjpeg-dev libtiff-dev libxxf86vm1 libxxf86vm-dev libxi-dev libxrandr-dev

如果您想查看视图图 svg 日志，请安装 Graphviz。

$ sudo apt-get install graphviz

2.查看 OpenMVG。

$ git clone --recursive https://github.com/openMVG/openMVG.git

$ mkdir openMVG_Build && cd openMVG_Build

3.配置和构建
$ cmake -DCMAKE_BUILD_TYPE=RELEASE ../openMVG/src/   -DOpenMVG_BUILD_TESTS=ON

$ cmake --build . --target install

使用 make 或 ctest 运行测试（如果在 CMake 命令行中使用 请求-DOpenMVG_BUILD_TESTS=ON）

$ make test

$ ctest --output-on-failure -j



openMvs安装:

1.eigen 线性算术的C++模板库

需要装4.0
tar -xzvf eigen-3.4.0 .tar.gz

cd eigen-3.4.0

mkdir build

cd build
cmake ..
sudo make
sudo make install
2.OPENCV 跨平台计算机视觉库
sudo apt install libopencv-dev

3.CGAL 计算几何算法库(CGAL)是一个高效可靠的C++几何算法库
sudo apt-get install libcgal-dev

4.安装boots C++程序库
sudo apt-get install libboost-dev
或
下载最新tar.gz
tar -zxvf boost_1_84_0.tar.gz 
cd boost_1_84_0/
sudo ./bootstrap.sh --with-libraries=all --with-toolset=gcc
sudo ./b2 toolset=gcc
sudo ./b2 install
sudo ldconfig    


5.vcglib 2020年的版本
git clone https://github.com/cdcseacave/VCG.git vcglib

11 glog 手动安装
git clone https://github.com/google/glog.git
cd glog
git checkout v0.4.0
mkdir build && cd build
cmake ..
make -j4
make install


6.ceres 用于建模和解决大型复杂的优化问题
依赖
# CMake
sudo apt-get install cmake
# gflags
sudo apt-get install libgflags-dev
# Use ATLAS for BLAS & LAPACK
sudo apt-get install libatlas-base-dev
# Eigen3
参照上边
# SuiteSparse (optional)
sudo apt-get install libsuitesparse-dev
安装
git clone https://github.com/ceres-solver/ceres-solver.git

mkdir ceres-bin
cd ceres-bin
cmake ../ceres-solver

 ###ln -s /usr/include/eigen3/Eigen /usr/include/Eigen
make -j3
make test
# Optionally install Ceres, it can also be exported using CMake which
# allows Ceres to be used without requiring installation, see the documentation
# for the EXPORT_BUILD_DIR option for more information.
make install





7#GLFW3 (Optional)
apt-get -y install freeglut3-dev libglew-dev libglfw3-dev


8 colmap
sudo apt-get install \
    git \
    cmake \
    ninja-build \
    build-essential \
    libboost-program-options-dev \
    libboost-filesystem-dev \
    libboost-graph-dev \
    libboost-system-dev \
    libflann-dev \
    libfreeimage-dev \
    libmetis-dev \
    libgtest-dev \
    libsqlite3-dev \
    libglew-dev \
    qtbase5-dev \
    libqt5opengl5-dev \
    libcgal-dev 


git clone https://github.com/colmap/colmap.git
cd colmap
mkdir build
cd build

cmake .. -GNinja -DCMAKE_CUDA_ARCHITECTURES=all                                                                                                                                                      
ninja
sudo ninja install

9安装openMvs
#Clone OpenMVS 需要切换到develop分支
git clone --recurse-submodules https://github.com/cdcseacave/openMVS.git
#Make build directory:
mkdir openMVS_build
cd openMVS_build

#Run CMake:个
cmake . ../openMVS -DCMAKE_BUILD_TYPE=Release -DVCG_ROOT="/home/vcglib"
#build install:
注释掉 libs/Common/Types.inl 中 zstd 相关的代码。
#include <boost/iostreams/filter/zstd.hpp>
make -j2 && make install

//报错ZSTD相关 ，需要注释掉Types.inl中相关代码

#环境变量
export VCG_ROOT=/home/vcglib
export VCPKG_HOME=/home/vcpkg
export openMVG=/home/openMVG_Build/Linux-x86_64-RELEASE/
export colmap=/home/colmap
export openMVS=/home/openMVS_build/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64
export CAMERA_SENSOR_DB_DIRECTORY=/home/openMVG/src/openMVG/exif/sensor_width_database
export PATH=$PATH:$VCPKG_HOME:$VCG_ROOT:$openMVG:$openMVS:$colmap:$CAMERA_SENSOR_DB_DIRECTORY
