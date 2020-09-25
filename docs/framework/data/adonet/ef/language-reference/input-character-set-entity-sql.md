---
title: Giriş karakter kümesi (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
ms.openlocfilehash: 94615a8f4aec51347f451d6f6a53b9d5b459a336
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203663"
---
# <a name="input-character-set-entity-sql"></a>Giriş karakter kümesi (Entity SQL)

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] UTF-16 ' da kodlanmış UNICODE karakterlerini kabul eder.  
  
 Dize sabit değerleri, tek tırnak içine alınmış herhangi bir UTF-16 karakteri içerebilir. Örneğin, N ' 文字列リテラル '. Dize sabit değerleri karşılaştırıldığı zaman, özgün UTF-16 değerleri kullanılır. Örneğin, N'ABC ' Japonca ve Latin kod sayfalarında farklıdır.  
  
 Yorumlar herhangi bir UTF-16 karakteri içerebilir.  
  
 Kaçışlı tanımlayıcılar, köşeli ayraçlar içinde herhangi bir UTF-16 karakteri içerebilir. Örneğin, [エスケープされた識別子]. UTF-16 kaçışlı tanımlayıcıların karşılaştırması büyük/küçük harfe duyarlıdır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aynı görünen, ancak farklı kod sayfalarından farklı karakter olan harflerin sürümlerini değerlendirir. Örneğin, karşılık gelen karakterler aynı kod sayfasından ise [ABC], [abc] ile eşdeğerdir. Ancak, aynı iki tanımlayıcı farklı kod sayfalarından ise eşdeğer değildir.  
  
 Boşluk, UTF-16 boşluk karakteridir.  
  
 Yeni satır, normalleştirilmiş UTF-16 yeni satır karakteri olur. Örneğin, ' \n ' ve ' \r\n ' yeni satır karakterleri olarak değerlendirilir, ancak ' \r ' bir yeni satır karakteri değildir.  
  
 Anahtar sözcükler, ifadeler ve noktalama, Latin 'e normalleştirir UTF-16 karakteri olabilir. Örneğin, Japonca kod sayfasında SEÇIM geçerli bir anahtar sözcüktür.  
  
 Anahtar sözcükler, ifadeler ve noktalama yalnızca Latin karakter olabilir. `SELECT` Japonca kod sayfasında anahtar sözcük değildir. +,-, \* ,/, =, (,), ', [,] ve burada tırnak içine alınmış diğer dil yapısı yalnızca Latin karakter olabilir.  
  
 Basit tanımlayıcılar yalnızca Latin karakter olabilir. Bu, özgün değerler karşılaştırıldığından karşılaştırma sırasında karışıklığı önler. Örneğin, ABC Japonca ve Latin kod sayfalarında farklı olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
