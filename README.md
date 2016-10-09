# CrackDex

#迄今为止的DEX加壳方案

    classes.dex整包加密：整包加密即直接加密整个DEX文件保存在其他目录，运行时脱壳机解密还原出classes.dex。
        
    classes.dex字节码变形：字节码变形会对classes.dex文件进行预处理，如抽出Method等信息进行加密，并存放在不同的文件中，运行时脱壳机将Method解密并恢复到classes.dex中。
    VMProtect: 将关键代码编译为专用虚拟机代码，于专用虚拟机中执行，这种方式正在研发中，也可能是未来的发展方向。
        
#脱壳方法

    1.手动脱壳，最费时费力的方式，但是对任何壳都通用。
    2.内存dump，适用于所有的整包加密，直接通过匹配dex.035关键字，dump出解密后的classes.dex文件即可。
    3.在class加载时dump出dex有关数据再重组，通过修改android源码，在程序运行时进行脱壳。
    4.在Dalvik解释执行时进行插桩，即加入Probe探针，获取运行时信息进行监控脱壳。
    
#现有脱壳方法的缺陷
    
    1.手动脱壳： 费时费力
    2.内存dump： 如果dex只是在运行时才解密该段代码就脱不出正确的classes.dex，或者加壳方将magic字段去掉，匹配不了关键字，也不能正确脱壳。
    3.在classes加载时dump出dex有关的数据再重组： 需要制定脱壳完成时的标志，但是这些对加固者来说是很容易改变的，并不能做到特别通用。
    4.在Dalvik解释执行时进行插桩： 兼容性不好，不能适用于所有的android版本。如Indroid，不支持JIT模式，底层涉及很多，需要很强的基本功。
    
#需要解决的问题
    
    1.兼容性
    2.通用性
    3.高效性
    4.有没有更通用的脱壳方式
    
#CrackDex

    结合以上脱壳方式的优缺点，或者自己提出新的通用方案，解决存在的问题。