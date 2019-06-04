## CMakeLists 详解

#### 基础语法

```c++
1.cmake_minimum_required(VERSION 2.8)
  // 指定cmake的最低版本
2.project(<projectname> [languageName1 languageName2 ...])
  // projectname：工程名
  // languageName：指定工程可以支持的语言。
3.set( CMAKE_CXX_FLAGS "-std=c++11" )
  // 添加标准支持
4.find_package(OpenCV 2.4.3 REQUIRED)
  // 包的名称及最低版本
5.include_directories()
    ${PROJECT_SOURCE_DIR}
    ${PROJECT_SOURCE_DIR}/include
    ${EIGEN3_INCLUDE_DIR}
	// 包含路径
6.set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/lib)
  // 设置路径（下面生成共享库的路径），即生成的共享库在工程文件夹下的lib文件夹中
7.add_library(${PROJECT_NAME} SHARED src/cpp文件名 …… ）
		${PROJECT_NAME}是生成的库名 表示生成的共享库文件就叫做 lib工程名.so  
	// 创建共享库（把工程内的cpp文件都创建成共享库文件，方便通过头文件来调用）
8.target_link_libraries(${PROJECT_NAME} /usr/lib/i386-linux-gnu/libboost_system.so )
  // 链接库，把刚刚生成的${PROJECT_NAME}库和所需的其它库链接起来
9.set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)
  // 设置可执行文件生成路径
10.add_executable(要生成的可执行文件名 从工程目录下写起的主函数文件名)
  // 可执行文件生成,凡是要编译的源文件都需要列举出来            
11.target_link_libraries(可执行文件名 ${PROJECT_NAME})              
	// 这个添加可执行文件所需的库（一般就是刚刚生成的工程的库），比如我们用到了libm.so（命名规则：lib+name+so）,就添加该库的名称"m"
```



### C++工程创建流程

```c++
$mkdir hellotest

$cd hellotest

$mkdir bin #可执行文件存放路径

$mkdir lib  #生成的.so文件存放路径

$mkdir include #头文件存放路径

$mkdir src #源文件存放路径

$mkdir build #编译文件存放路径

$touch CMakeLists.txt

$cd build

$cmake ..

$make
```


