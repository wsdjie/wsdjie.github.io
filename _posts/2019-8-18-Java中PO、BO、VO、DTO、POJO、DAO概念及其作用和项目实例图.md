---
layout:     post
title:      "Java中PO、BO、VO、DTO、POJO、DAO概念及其作用和项目实例图（转）"
subtitle:   ""
date:       2019-08-18-15:00:00
author:     ""
header-img: "img/bg3.jpg"
tags:
  - 后端
  - 开发
---

### Java中PO、BO、VO、DTO、POJO、DAO概念及其作用和项目实例图（转）

<div id="cnblogs_post_body" class="blogpost-body ">
    <p><strong>PO（bean、entity等命名）：</strong></p>
<p class="_mce_tagged_br">Persistant Object持久对象，数据库表中的记录在java对象中的显示状态</p>
<p class="_mce_tagged_br">最形象的理解就是一个PO就是数据库中的一条记录。</p>
<p class="_mce_tagged_br">好处是可以把一条记录作为一个对象处理，可以方便的转为其它对象。&nbsp;</p>
<p><strong>BO（service、manager、business等命名）： </strong></p>
<p>Business Object业务对象</p>
<p>主要作用是把业务逻辑封装为一个对象。这个对象可以包括一个或多个其它的对象。</p>
<p>形象描述为一个对象的形为和动作，当然也有涉及到基它对象的一些形为和动作。比如处理</p>
<p>一个人的业务逻辑，有睡觉，吃饭，工作，上班等等形为还有可能和别人发关系的形为。</p>
<p>这样处理业务逻辑时，我们就可以针对BO去处理。</p>
<p><strong>VO（from也有此写法） ：</strong></p>
<p>Value Object值对象</p>
<p>主要体现在视图的对象，对于一个WEB页面将整个页面的属性封装成一个对象。然后用一个VO对象在控制层与视图层进行传输交换。</p>
<p><strong>DTO (经过处理后的PO，可能增加或者减少PO的属性)：</strong></p>
<p>Data Transfer Object数据传输对象</p>
<p>主要用于远程调用等需要大量传输对象的地方。</p>
<p>比如我们一张表有100个字段，那么对应的PO就有100个属性。</p>
<p>但是我们界面上只要显示10个字段，</p>
<p>客户端用WEB service来获取数据，没有必要把整个PO对象传递到客户端，</p>
<p>这时我们就可以用只有这10个属性的DTO来传递结果到客户端，这样也不会暴露服务端表结构.到达客户端以后，如果用这个对象来对应界面显示，那此时它的身份就转为VO&nbsp;</p>
<p><strong>POJO（POJO是一种概念或者接口，身份及作用随环境变化而变化） ： </strong></p>
<p>POJO有一些Private的参数作为对象的属性。然后针对每个参数定义了get和set方法作为访问的接口</p>
<p>Plain Ordinary Java Object简单Java对象</p>
<p>即POJO是一个简单的普通的Java对象，它不包含业务逻辑或持久逻辑等，但不是JavaBean、EntityBean等，不具有任何特殊角色和不继承或不实现任何其它Java框架的类或接口。</p>
<p>POJO对象有时也被称为Data对象，大量应用于表现现实中的对象。&nbsp;</p>
<p>一个POJO持久化以后就是PO。</p>
<p>直接用它传递、传递过程中就是DTO</p>
<p>直接用来对应表示层就是VO&nbsp;</p>
<p><a href="https://images2018.cnblogs.com/blog/417876/201712/417876-20171203232709851-347591406.png" title="点击查看原图" target="_blank" class="aimg"><img src="https://images2018.cnblogs.com/blog/417876/201712/417876-20171203232709851-347591406.png" alt=""></a></p>
<p><strong>DAO（Data Access Object数据访问对象）：</strong></p>
<p>这个大家最熟悉，和上面几个O区别最大，基本没有互相转化的可能性和必要.</p>
<p>主要用来封装对数据库的访问。通过它可以把POJO持久化为PO，用PO组装出来VO、DTO</p>
<p><strong>Controller控制层主要是Action/Servlet等构成（目前Spring MVC则是通过@Controller标签使用）</strong></p>
<p>此层业务层与视图层打交道的中间层，负责传输VO对象和调用BO层的业务方法，负责视图层请求的数据处理后响应给视图层。</p>
<p><strong>View（视图层）</strong></p>
<p>主要是指由JSP、HTML等文件形成的显示层。</p>
<p>总结一下要用具体的X0需要看具体环境及项目架构，在不同的层、不同的应用场合，对象的身份也不一样，而且对象身份的转化也是很自然的。就像你对老婆来说就是老公，对父母来说就是子女。设计这些概念的初衷不是为了唬人而是为了更好的理解和处理各种逻辑，让大家能更好的去用面向对象的方式处理问题。</p>
<p>在平时开发项目中大家千万过度设计各层，因为这样会带来大量的工作和重复工作。如果不是大型系统可简化一些层，因为技术是为应用服务的。</p>
<div>
<p><strong>上述名词在实际项目的应用举例：</strong></p>
<p class="_mce_tagged_br">控制层(controller-action)，业务层/服务层( bo-manager )，实体层(po-entity)，dao(dao)，视图对象(Vo-本项目省略)，视图层(view-jsp/html)</p>
<p class="_mce_tagged_br"><a href="https://images2018.cnblogs.com/blog/417876/201712/417876-20171203232655741-434600538.png" title="点击查看原图" target="_blank" class="aimg"><img src="https://images2018.cnblogs.com/blog/417876/201712/417876-20171203232655741-434600538.png" alt=""></a></p>
<p>&nbsp;</p>
<p class="_mce_tagged_br">&nbsp;</p>
</div>
<p>参考：</p>
<p><a href="http://www.360doc.com/content/14/1225/14/15242507_435666535.shtml" target="_blank">http://www.360doc.com/content/14/1225/14/15242507_435666535.shtml</a>（以上内容转自此篇文章）</p>
<p>&nbsp;</p>
</div>