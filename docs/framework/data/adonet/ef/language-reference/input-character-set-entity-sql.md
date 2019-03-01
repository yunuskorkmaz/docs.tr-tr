---
title: Giriş karakter kümesi (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
ms.openlocfilehash: 7bed10f6e4a9fb01abe825e5eb798da2d866ca84
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976765"
---
# <a name="input-character-set-entity-sql"></a>Giriş karakter kümesi (varlık SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] UTF-16 kodlamalı UNICODE karakterler kabul eder.  
  
 Dize sabit değerlerinin tek tırnak içinde herhangi bir UTF-16 karakter içerebilir. Örneğin, N '文字列リテラル'. Dize değişmez değerleri karşılaştırıldığında, özgün UTF-16 değerlerin kullanılır. Örneğin, N'ABC' Japonca ve Latin kod sayfaları farklıdır.  
  
 Açıklamalar, herhangi bir UTF-16 karakter içerebilir.  
  
 Atlatmalı tanımlayıcılar, köşeli ayraçlar içinde herhangi bir UTF-16 karakter içerebilir. Örneğin, [エスケープされた識別子]. UTF-16 Atlanan tanımlayıcı karşılaştırması büyük/küçük harf ve büyük harflere duyarlı değildir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aynı görünür, ancak farklı bir karakter olarak farklı kod sayfalarından olan harf sürümleri değerlendirir. Örneğin, aynı kod sayfasından karşılık gelen karakterler yer alıyorsa [ABC] [abc] için eşdeğerdir. Aynı iki farklı kod sayfalarını tanımlayıcılardır, ancak eşdeğer değiller.  
  
 Boşluk herhangi UTF-16 boşluk karakteridir.  
  
 Yeni bir satır normalleştirilmiş UTF-16 yeni satır karakterleri ' dir. Örneğin, yeni satır karakteri, '\n' ve '\r\n' olarak kabul edilir, ancak '\r' bir yeni satır karakteri değil.  
  
 Anahtar sözcükler, ifadeler ve noktalama işaretleri için Latin normalleştirir herhangi bir UTF-16 karakter olabilir. Örneğin, Japonca bir kod seçin, geçerli bir anahtar sözcüktür.  
  
 Anahtar sözcükler, ifadeler ve noktalama işaretleri, yalnızca Latin karakterler olabilir. `SELECT` Japonca bir kod sayfasına bir anahtar değil. +,-, \*, /, =, (,), ', [,] ve burada tırnak işareti olmayan diğer dil yapısı yalnızca Latin karakterler olabilir.  
  
 Basit tanımlayıcı yalnızca Latin karakterler olabilir. Özgün değer karşılaştırıldığı bu karşılaştırma sırasında belirsizliği ortadan kaldırır. Örneğin, ABC Japonca ve Latin kod sayfaları farklı olacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
