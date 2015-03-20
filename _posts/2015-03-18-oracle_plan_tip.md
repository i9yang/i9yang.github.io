---
layout: post
title:  "oracle plan"
date:   2015-03-18
---

  ALTER SESSION SET STATISTICS_LEVEL = ALL; 

  SELECT * FROM TABLE(DBMS_XPLAN.DISPLAY_CURSOR(NULL,NULL,'ALLSTATS LAST'));   
-- 마지막 실행 쿼리에 대한 실측 정보 보기

[plan_tool](https://github.com/i9yang/i9yang.github.io/tree/master/_posts/plan_tool.pdf)




