Use pkg-config
==============

在命令行中
----------

* 直接在命令行中使用\ ``pkg-config``\ 命令查看库的信息:

  .. code-block:: sh
    :emphasize-lines: 1

    pkg-config --cflags --libs xxx

* 在命令行的编译命令中, 使用反单引号包裹\ ``pkg-config``\ 命令部分.

  Assuming the *x* library has a ``x.pc`` pkg-config file, use the following compiler command line:

  .. code-block:: sh 
    :emphasize-lines: 1

    cc `pkg-config --cflags --libs x` -o myapp myapp.c


在Qt项目中
----------
``qmake`` can configure the build process to take advantage of external libraries that are supported by ``pkg-config``,
such as the *D-Bus* and *ogg* libraries, with the following line:

.. code-block:: sh
    :emphasize-lines: 1, 2

    CONFIG += link_pkgconfig
    PKGCONFIG += ogg dubs-1

在Qt pro文件中, 如果要使用 ``pkg-config`` 来导入支持 ``pkg-config`` 的外部库:

* 在pro文件中加入: ``CONFIG += link_pkgconfig``
* 使用 ``PKGCONFIG +=`` 语句添加要导入的库


在cmake构建的项目中
-------------------

