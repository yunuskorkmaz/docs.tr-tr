---
title: Kurallı matematik işlevleri
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9d823eb45babca4b8f5dd717b4fb92c1984d1c8c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765106"
---
# <a name="math-canonical-functions"></a>Kurallı matematik işlevleri
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Matematik kurallı işlevler içerir.  
  
 Aşağıdaki tabloda matematik gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`Abs(` `value` `)`|Mutlak değerini döndürür `value`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> Bir `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, ve `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `value`.<br /><br /> **Örnek**<br /><br /> `Abs(-2)`|  
|`Ceiling(` `value` `)`|Daha az değil en küçük tamsayıyı döndürür daha `value`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Single`, `Double`, ve `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `value`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
 [!code-sql[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]|  
|`Floor(` `value` `)`|Büyük değil en büyük tamsayıyı döndürür `value`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Single`, `Double`, ve `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `value`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
 [!code-sql[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]|  
|`Power(` `value`, `exponent``)`|Belirtilen sonucunu döndürür `value` belirtilen `exponent`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `value`: Bir `Int32, Int64, Double`, veya `Decimal`.<br /><br /> `exponent`: Bir `Int64``, Double`, veya `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `value`.<br /><br /> **Örnek**<br /><br /> `Power(748.58,2)`|  
|`Round(` `value` `)`|Tamsayı kısmını döndürür `value`, en yakın tamsayıya yuvarlanır.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Single`, `Double`, ve `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `value`.<br /><br /> **Örnek**<br /><br /> `Round(748.58)`|  
|`Round(` `value`, `digits``)`|Döndürür `value`, yuvarlanır yakın belirtilen `digits`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `value`: `Double` veya `Decimal`.<br /><br /> `digits`: `Int16` veya `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `value`.<br /><br /> **Örnek**<br /><br /> `Round(748.58,1)`|  
|`Truncate(` `value`, `digits``)`|Döndürür `value`ve kesilmiş için en yakın belirtilen `digits`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `value`: `Double` veya `Decimal`.<br /><br /> `digits`: `Int16` veya `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `value`.<br /><br /> **Örnek**<br /><br /> `Truncate(748.58,1)`|  
  
 Bu işlevler döndürülecek `null` verildiyse `null` giriş.  
  
 Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer işlevselliği kullanılabilir. Daha fazla bilgi için bkz: [SqlClient Entity Framework işlevleri için](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
