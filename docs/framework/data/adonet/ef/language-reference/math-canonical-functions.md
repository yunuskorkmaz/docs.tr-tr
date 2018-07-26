---
title: Kurallı matematik işlevleri
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: c61db6d977614b95ea507b38c3890f2da8228158
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199314"
---
# <a name="math-canonical-functions"></a>Kurallı matematik işlevleri
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı matematik işlevleri içerir.  
  
 Aşağıdaki tabloda, matematik gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevler.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`Abs(value)`|Mutlak değerini döndürür `value`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> Bir `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, ve `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `value`.<br /><br /> **Örnek**<br /><br /> `Abs(-2)`|  
|`Ceiling(value)`|Küçük olmayan en küçük tamsayı döndürür daha `value`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Single`, `Double`, ve `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `value`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)] <br /><br /> [!code-sql[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]|  
|`Floor(value)`|Değerinden büyük olmayan en büyük tamsayı döndürür `value`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Single`, `Double`, ve `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `value`.<br /><br /> **Örnek**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)] <br /><br /> [!code-sql[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]|  
|`Power(value, exponent)`|Belirtilen sonuç döndüren `value` belirtilen `exponent`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `value`: Bir `Int32, Int64, Double`, veya `Decimal`.<br /><br /> `exponent`: Bir `Int64`, `Double`, veya `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `value`.<br /><br /> **Örnek**<br /><br /> `Power(748.58,2)`|  
|`Round(value)`|Tamsayı bölümünü döndürür `value`, en yakın tamsayıya yuvarlanır.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Single`, `Double`, ve `Decimal`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `value`.<br /><br /> **Örnek**<br /><br /> `Round(748.58)`|  
|`Round(value, digits)`|Döndürür `value`, yuvarlanır yakın belirtilen `digits`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `value`: `Double` veya `Decimal`.<br /><br /> `digits`: `Int16` veya `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `value`.<br /><br /> **Örnek**<br /><br /> `Round(748.58,1)`|  
|`Truncate(value, digits)`|Döndürür `value`, kesilmiş yakın belirtilen `digits`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `value`: `Double` veya `Decimal`.<br /><br /> `digits`: `Int16` veya `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `value`.<br /><br /> **Örnek**<br /><br /> `Truncate(748.58,1)`|  
  
 Bu işlevler döndüreceği `null` verildiyse `null` giriş.  
  
 Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer bir işlevselliği kullanılabilir. Daha fazla bilgi için [Entity Framework işlevleri için SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
