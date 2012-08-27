---
layout: post
title: "如何写出可维护的代码?"
description: "浮现式设计读书笔记"
category: "readingBook"
tags: [ "浮现式设计" , "随笔" ]
---
{% include JB/setup %}

### 代码必须条理清晰    
 
- 不因为改变系统中一部分代码，而给其他部分带来不好的影响（重构的有效性） 
- 需要做出改变时，调整哪里的代码应该显而易见    
- 修改代码后，应该能够验证你做出了想要的修改，并确认没有改变其他的部分

### **第一原则**     

第一原则是基本原则，其他原则都应遵循第一原则，第一原则是大量智慧的结晶，因此蕴含强大的力

>   ** 面向对象领域的第一原则： **

>   * 隐藏的可以改变（封装）
>   * 代码应仅实现应有的功能，而不必实现其他功能（内聚）

1. ### 封装

    可维护性是目标，既是这样一种能力：在修改代码时无需担心和迟疑，也不会感到有阻力。  
    将系统某一部分隐藏起来，使其他系统找不到他它，如此一来，避免了可能对其他部分造成的不可预见的伤害。

1. ### 内聚 
 
人们可能误解内聚（cohesion），因为听起来像聚合（adhesion——事物有多紧密地联系在一起） 

* 内聚表示系统内部对各个部分对同一问题的专注程度，以及这些部分彼此联系的紧密性。  
* 内聚的明显标志是为某个事物起名字的容易程度（eg：GUI团队——该团队都负责图形界面，有强大内聚力）  
  
  1. 方法内聚  
难于命名的方法是内聚性较差的典型信号  
将各自的步骤放入各自的方法中，主方法成为组织方法  

  2. 视角层的内聚  
内聚的另一个方面是方法在哪个视角层（level of perspective）执行操作的  
>   ** 三层视角《UML精萃》**
>
>   * 概念视角——呈现系统对象，理论上表示问题领域中的实体
>   * 规约视角——组成每个对象接口的公共方法，以及他们委派的私有方法，关心的是两个方法实现了什么，而不是如何实现
>   * 实现视角——考虑完成实际任务的代码
编写方法时，总是努力使它们具有一般意义上的内聚性——一个方法只解决一个问题的目的  

  3. 内类聚  
方法的内聚可以提高可读性，可维护性和条理性，类的内聚也是如此

