# Installing boost

```shell script
wget https://dl.bintray.com/boostorg/release/1.71.0/source/boost_1_71_0.tar.bz2
tar xfz boost_1_71_0.tar.gz
rm boost_1_71_0.tar.gz
cd boost_1_71_0
./bootstrap.sh --prefix=/usr/local --with-libraries=system,thread,program_options,filesystem,locale,iostreams
./b2 -j 8
cd ..
mv boost_1_71_0 /opt
ldconfig
```

#### Possibly you might need these

```shell script
export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/opt/boost_1_71_0/stage/lib
echo "export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/opt/boost_1_70_0/stage/lib" >> ~/.bashrc
```
