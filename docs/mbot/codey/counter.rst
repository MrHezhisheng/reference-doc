:mod:`codey_timer` --- 计数器
=============================================

.. module:: codey
    :synopsis: 计数器

``codey_timer`` 模块的主要功能与函数(因为是系统函数，所以使用时不需要带模块名称)

功能相关函数
----------------------

.. function:: get_timer()

   获取计时器当前值（计时器从用户脚本启动时开始运行），返回值是一个浮点数据，单位是 ``秒``。

.. function:: reset_timer()

   初始化计时器的值

Sample Code：
----------------------

.. code-block:: python

  import codey
  
  codey.reset_timer()
  
  while True:
      print("time:", end = "")
      print(codey.get_timer())