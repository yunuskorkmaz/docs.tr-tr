---
title: Tür tanımları (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 2e068db0ce202c26cad36c8ed7adf0acdfb8e363
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879560"
---
# <a name="type-definitions-entity-sql"></a>Tür tanımları (varlık SQL)
Bir tür tanımı bildirim deyiminde kullanılan bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] satır içi işlev.  
  
## <a name="remarks"></a>Açıklamalar  
 Bildirim deyimindeki bir satır içi işlevinin oluşan [işlevi](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) ayracından (parametre tanımı listesinde işlev adından (örneğin, "MyAvg") temsil eden tanımlayıcı ardından anahtar sözcüğü Örneğin, "Collection(Decimal)") sonu.  
  
 Sıfır veya daha fazla parametre tanımını parametre tanımı listesinden oluşur. Her parametre tanımında bir tür tanımı (örneğin, "Collection(Decimal)"). ardından bir tanımlayıcı (örneğin, "sonu" işlevine parametrenin adı) oluşur  
  
 Tür tanımlarını şöyle olabilir:  
  
- Tanımlayıcı (örneğin, "Int32" veya "AdventureWorks.Order") türü.  
  
- Anahtar sözcüğü `COLLECTION` parantez (örneğin, "Collection(AdventureWorks.Order)"). başka bir tür tanımında ardından  
  
- Anahtar sözcüğü satır parantez (örneğin, "Row(x AdventureWorks.Order)") içinde özellik tanımları listesi tarafından izlenen. Özellik tanımları sahip bir biçimi gibi "`identifier type_definition`, `identifier type_definition`,...".  
  
- Türü (örneğin, "Ref(AdventureWorks.Order)"). parantez içinde tanımlayıcısının arkasından REF anahtar sözcüğü Başvuru türü tanımı işleci, bağımsız değişken olarak bir varlık türü gerektirir. Basit bir tür bağımsız değişkeni olarak belirtemezsiniz.  
  
 Tür tanımları da iç içe geçirebilirsiniz (örneğin, "koleksiyonu (Row(x Ref(AdventureWorks.Order)))").  
  
 Tür tanımı seçenekleri şunlardır:  
  
- `IdentifierName supported_type`, veya  
  
- `IdentifierName` KOLEKSİYON (`type_definition`), veya  
  
- `IdentifierName` SATIR (`property_definition`), veya  
  
- `IdentifierName` REF (`supported_entity_type`)  
  
 Özellik tanımı seçeneği `IdentifierName type_definition`.  
  
 Geçerli ad alanındaki herhangi bir türü desteklenen türleridir. Bunlar, hem temel hem de varlık türleri içerir.  
  
 Varlık türleri yalnızca varlık türleri geçerli ad alanındaki bakın desteklenmiyor. İlkel türler dahil değildir.  
  
## <a name="examples"></a>Örnekler  
 Bir basit tür tanımı, bir örnek verilmiştir.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 Aşağıdaki KOLEKSİYON türü tanımı örneğidir.  
  
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
  
 Başvuru türü tanımı bir örnek verilmiştir.  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
