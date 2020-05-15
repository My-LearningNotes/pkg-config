Generate a pkg-config file from cmake
======================================

在一个cmake脚本中(\ ``pkg-config/CMakeLists.txt``\ 或\ ``cmake_modules/GeneratePkgconfigFile``\ ),
包含生成pkg-config file的cmake代码, 在项目根目录下的CMakeLists.txt\* 文件中, 包含该脚本.

需要一个用来生成pkg-config file的template file, 通常将该template file命名为: ``pkg-config.pc.in``, 在上述的cmake脚本中, 以该文件为模板, 生成pkg-config file;
在模板文件中, 可以使用cmake中的变量, 在cmake根据模板文件生成pkg-config file时, 将变量替换为实际的值.

在cmake根据模板文件生成pkg config-file时, 应该将文件名也同时修改为项目名.

.. code-block:: sh
    :emphasize-lines: 3, 5, 6, 7, 8, 10, 11, 12, 13, 14, 15

    # Template to generate a pkg-config file

    option(BUILD_PKGCONFIG "Build pkg-config file" ON)

    prefix=@CMAKE_INSTALL_PREFIX@
    exec_prefix=${prefix}
    includedir=
    libdir=

    Name:
    Description:
    URL:
    Version:
    Cflags:
    Libs:

.. note::

  在template file中, 以\ ``@VAR@``\ 的形式引用cmake中定义的变量.

