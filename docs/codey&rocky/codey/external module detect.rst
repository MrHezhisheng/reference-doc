:mod:`codey_external_module_detect` --- 模块接入检测
=============================================

.. module:: codey
    :synopsis: 模块接入检测

``codey_external_module_detect`` 模块的主要功能与函数(因为是系统函数，所以使用时不需要带模块名称)

功能相关函数
----------------------

.. function:: has_neuron_connected()

   检测是否有任何神经元模块接入小程，返回值是布尔值，其中 ``True`` 表示有神经元模块接入了小程(包括小奔的接入)，``False`` 表示没有任何神经元模块的接入。

.. function:: is_rocky_connected()

   检测小奔是否接入小程，返回值是布尔值，其中 ``True`` 表示有小奔接入了小程，``False`` 表示小奔没有接入。

程序示例：
----------------------

.. code-block:: python

  import codey
  import time
  
  while True:
      if codey.is_rocky_connected():
          print("rocky is in")
      else:
          print("rocky is out")
      time.sleep(1)