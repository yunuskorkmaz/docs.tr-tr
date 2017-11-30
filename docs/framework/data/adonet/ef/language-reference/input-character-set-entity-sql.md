---
title: "Giriş karakter kümesi (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 691f29a04b1b1f997be501330ec887d6815d7531
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="input-character-set-entity-sql"></a>Giriş karakter kümesi (varlık SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]UTF-16 kodlu UNICODE karakterler kabul eder.  
  
 Dize değişmez değerleri tek tırnak içine alınmış herhangi bir UTF-16 karakter içerebilir. Örneğin, N '文字列リテラル'. Dize değişmez değerleri karşılaştırıldığında, özgün UTF-16 değerler kullanılır. Örneğin, N'ABC' Japonca ve Latin kod sayfaları farklıdır.  
  
 Yorumlar herhangi bir UTF-16 karakter içerebilir.  
  
 Kaçış karakterli tanımlayıcılar köşeli ayraçlar içinde herhangi bir UTF-16 karakter içerebilir. Örneğin, [エスケープされた識別子]. UTF-16 kaçışlı tanımlayıcıları karşılaştırma büyük küçük harfe duyarlı. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]aynı görünür, ancak farklı karakter olarak farklı kod sayfalarından olan harf sürümlerini değerlendirir. Örneğin, aynı kod sayfasından karşılık gelen karakter ise [ABC] [abc] eşdeğerdir. Aynı iki farklı kod sayfaları tanımlayıcılardır, ancak eşdeğer değiller.  
  
 Beyaz alan tüm UTF-16 boşluk karakterdir.  
  
 Bir satır başı karakteri herhangi normalleştirilmiş UTF-16 yeni satır karakteri ' dir. Örneğin, '\n' ve '\r\n' satırbaşı karakterlerini olarak kabul edilir, ancak '\r' yeni satır karakteri değil.  
  
 Anahtar sözcükler, ifadeler ve noktalama için Latin normalleştirir herhangi bir UTF-16 karakter olabilir. Örneğin, Japonca codepage seçin, geçerli bir anahtar sözcüktür.  
  
 Anahtar sözcükler, ifadeler ve noktalama yalnızca Latin karakterler olabilir. `SELECT`Japonca kod sayfasında bir anahtar değil. +,-, *, /, =, (,), ', [,] ve burada tırnak içine alınmış değil başka bir dil yapısı yalnızca Latin karakterler olabilir.  
  
 Basit tanımlayıcıları yalnızca Latin karakterler olabilir. Özgün değerler karşılaştırıldığından bu karşılaştırma sırasında belirsizlik önler. Örneğin, ABC Japonca ve Latin kod sayfaları farklı olacaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık SQL genel bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
