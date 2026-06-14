Cascade文件是总体输入需放在DCU/CPU版本中使用

CPU为之前版本，基本正确，I团簇在8^4网格划分下在2e6时间仅有5%差异(Re,V团簇数量相对较少,其中Re团簇差异较大)

DCU为现在版本, 目前一个网格分给一个block。动态链表移植为扁平数组。但由于数据在 GPU 显存里，MPI 在 CPU 主存里。GPU 算完 Shell 后，必须经历 庞大显存回传 (D2H) $\rightarrow$ CPU 痛苦地重新寻址打包 $\rightarrow$ 发送 MPI 的串行过程。在这个过程中，GPU 被迫停机等待。且DCU运行操作时间异常长
