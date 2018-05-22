---
title: DOM基本操作
date: 2018-05-22 17:59:36
tags: DOM获取元素
---
#DOM获取元素对象的方法

##getElementById // 获取指定 ID的元素对象

    <div id="box"></div>
    document.getElementById('box');
    
##getElementsByClassName//可通过元素对象的class名字获取对象

   

     <div class="box"></div>
    document.getElementsByClassName('box');

##getElementsByTagName//通过HTML标签获取元素对象（注：得出的结果是和数组集合）

    <ul>
    <li></li>
    <li></li>
    <li></li>
    </ul>
    oLi = document.getElementsByTagName('li');

    // oLi得出的是数组集合 调用方法oLi[参数]
##querySelector //可通过元素对象ID和class获取出元素对象

<div class="box" id="box1"></div>

    document.querySelector('.box');
    querySelectorAll//获取一组元素