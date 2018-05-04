---
title: Giriş karakter kümesi (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
ms.openlocfilehash: 5e7886215cac2d9363a9ed68cd03a0fce4374055
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="input-character-set-entity-sql"></a>Giriş karakter kümesi (varlık SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] UTF-16 kodlu UNICODE karakterler kabul eder.  
  
 Dize değişmez değerleri tek tırnak içine alınmış herhangi bir UTF-16 karakter içerebilir. Örneğin, N '文字列リテラル'. Dize değişmez değerleri karşılaştırıldığında, özgün UTF-16 değerler kullanılır. Örneğin, N'ABC' Japonca ve Latin kod sayfaları farklıdır.  
  
 Yorumlar herhangi bir UTF-16 karakter içerebilir.  
  
 Kaçış karakterli tanımlayıcılar köşeli ayraçlar içinde herhangi bir UTF-16 karakter içerebilir. Örneğin, [エスケープされた識別子]. UTF-16 kaçışlı tanımlayıcıları karşılaştırma büyük küçük harfe duyarlı. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aynı görünür, ancak farklı karakter olarak farklı kod sayfalarından olan harf sürümlerini değerlendirir. Örneğin, aynı kod sayfasından karşılık gelen karakter ise [ABC] [abc] eşdeğerdir. Aynı iki farklı kod sayfaları tanımlayıcılardır, ancak eşdeğer değiller.  
  
 Beyaz alan tüm UTF-16 boşluk karakterdir.  
  
 Bir satır başı karakteri herhangi normalleştirilmiş UTF-16 yeni satır karakteri ' dir. Örneğin, '\n' ve '\r\n' satırbaşı karakterlerini olarak kabul edilir, ancak '\r' yeni satır karakteri değil.  
  
 Anahtar sözcükler, ifadeler ve noktalama için Latin normalleştirir herhangi bir UTF-16 karakter olabilir. Örneğin, Japonca codepage seçin, geçerli bir anahtar sözcüktür.  
  
 Anahtar sözcükler, ifadeler ve noktalama yalnızca Latin karakterler olabilir. `SELECT` Japonca kod sayfasında bir anahtar değil. +,-, *, /, =, (,), ', [,] ve burada tırnak içine alınmış değil başka bir dil yapısı yalnızca Latin karakterler olabilir.  
  
 Basit tanımlayıcıları yalnızca Latin karakterler olabilir. Özgün değerler karşılaştırıldığından bu karşılaştırma sırasında belirsizlik önler. Örneğin, ABC Japonca ve Latin kod sayfaları farklı olacaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
