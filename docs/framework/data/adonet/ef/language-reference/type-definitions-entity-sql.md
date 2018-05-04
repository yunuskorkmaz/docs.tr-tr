---
title: Tür tanımları (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 7abbe5dfed005a10955a385cadf12725a9450512
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="type-definitions-entity-sql"></a>Tür tanımları (varlık SQL)
Bir tür tanımı bildirimi deyiminde kullanılan bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] satır içi işlev.  
  
## <a name="remarks"></a>Açıklamalar  
 Satır içi işlev bildirimi deyimi oluşan [işlevi](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) parantez (için parametre tanımı listesinde işlevi adından (örneğin, "MyAvg") temsil eden tanımlayıcı arkasından anahtar sözcüğü Örneğin, "nedeniyle Collection(Decimal)").  
  
 Parametre tanımı listesi sıfır veya daha fazla parametre tanımlarını içerir. Her parametre tanımı bir tür tanımı (örneğin, "Collection(Decimal)"). ardından bir tanımlayıcı (örneğin, "sonu" işlevi için parametre adı) oluşur  
  
 Tür tanımları birini kullanabilir:  
  
-   Tanımlayıcı (örneğin, "Int32" veya "AdventureWorks.Order") türü.  
  
-   Anahtar sözcüğü `COLLECTION` parantez (örneğin, "Collection(AdventureWorks.Order)"). başka bir tür tanımında ve ardından  
  
-   Anahtar özellik tanımları parantez (örneğin, "Row(x AdventureWorks.Order)") içinde listesini satır arkasından. Özellik tanımları olan bir biçim gibi "`identifier type_definition`, `identifier type_definition`,...".  
  
-   Parantez (örneğin, "Ref(AdventureWorks.Order)"). tanımlayıcıda türünü ve ardından REF anahtar sözcüğü REF türü tanımı işleci bağımsız değişken olarak bir varlık türü gerektirir. Bağımsız değişken olarak bir ilkel türü belirtilemez.  
  
 Tür tanımları içe kullanabilirsiniz (örneğin, "koleksiyonu (Row(x Ref(AdventureWorks.Order)))").  
  
 Tür tanımı Seçenekler şunlardır:  
  
-   `IdentifierName supported_type`, veya  
  
-   `IdentifierName` KOLEKSİYON (`type_definition`), veya  
  
-   `IdentifierName` SATIR (`property_definition`), veya  
  
-   `IdentifierName` REF (`supported_entity_type`)  
  
 Özellik tanımı seçenek `IdentifierName type_definition`.  
  
 Desteklenen türler geçerli ad alanındaki tüm türleridir. Bunlar, ilkel ve varlık türleri içerir.  
  
 Yalnızca varlık türleri geçerli ad alanındaki türler başvurmak varlık desteklenir. İlkel türler içermez.  
  
## <a name="examples"></a>Örnekler  
 Aşağıda, bir basit tür tanımı bir örnektir.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 Bir KOLEKSİYON türü tanımının bir örnek verilmiştir.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 Satır türü tanımı bir örnek verilmiştir.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 REF türü tanımı bir örnek verilmiştir.  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
