-i 和 -o 选项
=============

``-i`` 和 ``-o`` 选项分别用于对输入和输出的数据进行列选择以及简单的代数运算。

经常遇到的情况是，已有的数据有很多列，而某个命令只需要其中的某几列；
或者某个命令的默认输出有很多列，却只想要输出其中的某几列。

``-i`` 选项可以从输入数据中选择任意列，并对其进行四则运算以及取对数操作。其语法为::

    -i<col>[+l][+s<scale>][+o<offset>][,...]

``-o`` 选项用于输出指定的列。其基本语法为::

    -o<col>[,...]

``-i`` 和 ``-o`` 选项后接以逗号分隔的列号（列号从0开始）或列号范围，以指定输入/输出
数据中需要保留的列及其顺序。列号范围的格式为 ``<start>[:<inc>]:[<stop>]``\ ，
若省略 ``<inc>`` 则默认其值为1。

对于 ``-i`` 选项而言，每个列号后还可以加上子选项以对每列数据进行简单的代数运算：

- ``+l`` 表示对当前列取 :math:`\log_{10}`
- ``+s<scale>`` 表示将当前列乘以比例因子 ``<scale>``
- ``+o<offset>`` 表示将当前列的值加上 ``<offset>``

举几个例子：

- ``-i3,6,2`` 表示读入数据中的第4、7、3列
- ``-o3,1,3`` 表示输出数据中的第4、2、4列，即第四列会被输出两次
- ``-i1-3,5`` 表示读入数据中的2-4列和第6列
- ``-i2+s2+o10,6,3`` 表示读入数据的第3、7、4列，并对第3列数据乘以2再加上10。
