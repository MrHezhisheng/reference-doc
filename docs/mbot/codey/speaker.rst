:mod:`speaker` --- 板载扬声器
=============================================

.. module:: speaker
    :synopsis: 板载扬声器

``speaker`` 模块的主要功能与函数

功能相关函数
----------------------

.. function:: stop_sounds()

   停止所有声音。

.. function:: play_melody(file_name)

   播放音频文件，该函数播放时，不会阻塞，但连续调用的话，后一次播放操作会停止前一次的播放，参数：

    - *file_name* 字符串类型，烧录在程小奔flash中的wav格式的音频文件名，输入时，也可省略格式的后缀 ``.wav``。
     可选择的音效文件有
::

     hello.wav       ： hello（哈喽）
     hi.wav          ： hi（嗨）
     bye.wav         ： bye（拜）
     yeah.wav        ： yeah（耶）
     wow.wav         ： wow（哇哦）
     laugh.wav       ： laugh（笑声）
     hum.wav         ： hum（哼唱）
     sad.wav         ： sad（难过）
     sigh.wav        ： sigh（叹气）
     annoyed.wav     ： annoyed（哼）
     angry.wav       ： angry（生气）
     surprised.wav   ： scared（惊吓）
     yummy.wav       ： pettish（撒娇）
     curious.wav     ： curious（好奇）
     embarrassed.wav ： embarrassed（尴尬）
     ready.wav       ： ready（准备）
     sprint.wav      ： sprint（冲刺）
     sleepy.wav      ： snore（打呼）
     meow.wav        ： meow（喵）
     start.wav       ： start（启动）
     switch.wav      ： switch（开关）
     beeps.wav       ： beeps（哔哔）
     buzzing.wav     ： buzz（蜂鸣）
     exhaust.wav     ： air-out（排气）
     explosion.wav   ： explosion（爆炸）
     gotcha.wav      ： gotcha（获取）
     hurt.wav        ： painful（痛苦）
     jump.wav        ： jump（跳动）
     laser.wav       ： laser（激光）
     level up.wav    ： level-up（升级）
     low energy.wav  ： low-energy（低能量）
     metal clash.wav ： metal-clash（金属音）
     prompt tone.wav ： prompt-tone（提示）
     right.wav       ： right（正确）
     wrong.wav       ： wrong（错误）
     ring.wav        ： ringtone（铃声）
     score.wav       ： score（得分）
     shot.wav        ： shot（发射）
     step_1.wav      ： step_1（脚步声1）
     step_2.wav      ： step_2（脚步声2）
     wake.wav        ： activate（激活）
     warning.wav     ： warning（警告）

.. function:: play_melody_until_done(file_name)

   播放音频文件直到停止，该函数会阻塞播放，即在未播放完音效之前，后一条指令无法得到执行，参数：

    - *file_name* 字符串类型，烧录在程小奔flash中的wav格式的音频文件名，输入时，也可省略格式名 ``.wav``，具体可选参数见 ``play_melody``。

.. function:: play_note(note_num, beat = None)

   播放音符， 数字音符定义请参考： `scratch数字音符说明 <https://en.scratch-wiki.info/wiki/Play_Note_()_for_()_Beats_(block)>`_，参数：

    - *note_num* 数值型，数值范围 ``48 - 72``，或者字符串类型，如 ``C4``。
    - *beat* 数值数据，表示节拍数，如果不填，则一直播放。
     音符与频率的对应关系如下::

     ['C2','65'],   ['D2','73'],   ['E2','82'],   ['F2','87'],
     ['G2','98'],   ['A2','110'],  ['B2','123'],  ['C3','131'],
     ['D3','147'],  ['E3','165'],  ['F3','175'],  ['G3','196'],
     ['A3','220'],  ['B3','247'],  ['C4','262'],  ['D4','294'],
     ['E4','330'],  ['F4','349'],  ['G4','392'],  ['A4','440'],
     ['B4','494'],  ['C5','523'],  ['D5','587'],  ['E5','659'],
     ['F5','698'],  ['G5','784'],  ['A5','880'],  ['B5','988'],
     ['C6','1047'], ['D6','1175'], ['E6','1319'], ['F6','1397'],
     ['G6','1568'], ['A6','1760'], ['B6','1976'], ['C7','2093'],
     ['D7','2349'], ['E7','2637'], ['F7','2794'], ['G7','3136'],
     ['A7','3520'], ['B7','3951'], ['C8','4186'], ['D8','4699'],

.. function:: play_tone(frequency, time = None)

   播放设定频率的声音，参数：

    - *frequency* 数值数据，播放声音的频率，其数值范围是 ``0 ~ 5000``。
    - *time* 数值数据，表示播放时间(单位是 ``毫秒-ms`` )，其数值范围是 ``0 ~ 数值范围极限``。

.. function:: rest(number)

   停止节拍，参数：

    - *number* 数值数据，暂停的节拍数，其数值范围是 ``0 ~ 数值范围极限``。

常量
----------------------

.. data:: speaker.volume

   数值数据，音量的大小的属性值，可以修改或者读取这个值。修改这个数值，可以控制音量的大小。其数值范围是 ``0 ~ 100``。

.. data:: speaker.tempo

   数值数据，表示播放速度的属性，单位是 ``bmp`` (beat per minute)，即每一个节拍的长度。  其数值范围是 ``6 ~ 600``。 默认数值是60，即一个节拍的维持时间是1秒。 ``rest`` 和 ``play_note`` 函数的节拍会受该常量影响。

程序示例：
----------------------

.. code-block:: python

  import codey
  import time
  
  codey.speaker.play_melody("hello", True)
  codey.display.show("hello")
  codey.display.clear()
  
  codey.speaker.play_note(48, 1)
  codey.speaker.rest(1)
  codey.display.show("note")
  codey.display.clear()
  codey.speaker.play_note("C4", 1)
  codey.speaker.rest(1)
  codey.display.show("C4")
  codey.display.clear()
  codey.speaker.play_tone(1000, 2)
  codey.speaker.rest(1)
  codey.display.show("tone")
  codey.display.clear()
  print("tempo:", end = "")
  print(codey.speaker.tempo)
  codey.speaker.play_note("C4", 1)
  codey.speaker.rest(1)
  codey.speaker.tempo = 120
  codey.speaker.volume = 20
  codey.speaker.play_note("C4", 1)
  codey.speaker.rest(1)
