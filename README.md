# Office-User-Auto-Create
with cloudflare workers

new demo at https://office-user-auto-create.zaya.workers.dev/

# Changelog
Rewrote web page with React，use KV to store codes

# Usage

[<img src="https://camo.githubusercontent.com/6eb04703e85da31c430de46d32a904a7c55c0b3bc00811ae689f14faf91cd32e/68747470733a2f2f6465706c6f792e776f726b6572732e636c6f7564666c6172652e636f6d2f627574746f6e">](https://deploy.workers.cloudflare.com/?url=https://github.com/zayabighead/Office-User-Auto-Create)

create a KV with namespace `_KV`

1: 按照原版教程取得 tenantId clientId clientSecret skuid
https://github.com/zayabighead/Office-User-Auto-Create/tree/master/archive

2: 新增worker，把项目中 worker.js 的东西全部copy过去

3: 根据自身情况修改config


4: 记得改掉 genCodesPassword ，不然别人可以帮你产生很多激活码

5: 在开头补上这一段

    addEventListener('fetch', event => {
      event.respondWith(handleRequest(event.request))
    })

复制代码


6: 新增KV，名称随意

7: 用 "_KV" 去绑定命名空间


8: 按需求改code。我要激活码可重复使用，我就把 code.delete() 部份给删掉了


9: 新增激活码: 去KV空间编辑，或是访问 genCodesPassword


10: 使用时，激活码就是 Key@Value


11: Demo: https://2gfre.kskb.eu.org/

顺便在博客也记录了一下过程
https://www.kskb.eu.org/2021/02/office-user-auto-create.html/
