# VASP_script
1.  2unix.sh
VASP INCAR里的tab输入程序是不认识的，往往会忽略这条参数，   可以将INCAR的格式转为UNIX的格式，同时可以将tab转为空格。 bash 2unix.sh INCAR
vaspkit109功能支持该功能，一键处理并检查vaspkit输入文件。

2.  animate-neb-xyz.sh
~~NEB插点后，将各个文件夹中的POSCAR.xyz组合成total.xyz，可以用VMD看动画。 bash animate-neb-xyz.sh ~~vaspkit0.72版 504功能已经支持该功能。405功能可以将XDATCAR转成PDB文件，支持用VMD软件可视化。

3. deltaer
查看RMM优化是否超过40步，如果超过，很可能SCF没有收敛。同时返回第一步和最后一步电子步的能量差值  bash deltaer

4. er
输出最后一步能量  bash er

5. fermi
输出fermi能级和轨道排布   bash fermi

6. kpoint
生成普通的K点，  bash kpoint G 4 4 4  等，对于高对称K点的生成推荐使用vaspkit。

7.merge_band.py
~~因为p4vasp 导出的能带和dos的 dat文件没有分开，没法用Origin直接绘图， python merge_band.py 可以重新将dat文件转化为 Origin可以直接绘图的dat文件。~~
vaspkit0.72版开始已经支持了导入格式兼容ORIGIN的dat文件，同时可以直接调用Python绘制DOS图，能带图。不再建议使用该辅助脚本。

8. OUTCAR2jmol.sh
针对JMOL可视化OUTCAR的频率振动时无法认识原子的问题。 bash OUTCAR2jmol.sh

9. POTCAR.sh 和 pos2pot
在POTCAR.sh中配置好赝势库的位置，再在pos2pot中配置好POTCAR.sh的位置， bash pos2pot 就可以根据POSCAR	中的元素信息自动生成POTCAR，如需要其他种类的 POTCAR，只需在POSCAR 的元素栏中将元素类型改成想用的赝势类型   比如 Li_pv。 vaspkit 1 功能已经支持 生成POTCAR，检查输入文件。

10. readbandgap.sh
计算能隙 bash readbandgap.sh

11. revi2-entropy.py  不再推荐 bash zpe
~~根据振动分析结果，计算处给定温度下的 H TS ZPE校正~~  vaspkit 5功能支持该功能，不仅可以计算气体自由能校正，还可以计算吸附质的自由能校正   

12. POSCARtoolkit.py
转化分数坐标；根据层数固定原子；选择性放开，固定或者部分固定原子 vaspkit 4 功能亦支持该功能，

13. sigma
可以自动判断sigma的取值是否合适。SIGMA 的取值要保证OUTCAR 中的 entropy T*S 这一项,平均到每个原子上,要小于 1-2 meV   bash sigma

14. Auxiliary Tool for the VASPKIT.rar
~~类似7， 将 vaspkit的输出文件转成 Origin的格式，同时另外的工具可以找出能带图中高对称点在能带图中的 x坐标。~~
vaspkit0.72版开始已经支持了导入格式兼容ORIGIN的dat文件，同时可以直接调用Python绘制DOS图，能带图。不再建议使用该辅助脚本。

15. cif2pos.py
将含有对称性信息的CIF文件转化成POSCAR。

16. xsd2pos.py
将含有fractional位置限制信息的xsd文件转成POSCAR。

17.XDATCAR_manipulation.py
读取vasp第一性原理动力学轨迹XDATCAR并提取能量，温度曲线，预留了接口输出每一帧的坐标

18.POSCAR_manipulation.py
读取和写出POSCAR的Python类封装。

19.半衰期.py
根据能垒计算一级反应的反应速率和反应半衰期

20.mp2incar.py
将Materials Project上的INCAR输入参数整合成规范的格式。
