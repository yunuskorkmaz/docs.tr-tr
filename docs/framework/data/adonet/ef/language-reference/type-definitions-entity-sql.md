---
title: Tür tanımları (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 7e4e6f0e9f64816d10a69a8b0639728e4cd7af80
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201024"
---
# <a name="type-definitions-entity-sql"></a>Tür tanımları (Entity SQL)

Bir tür tanımı, bir satır içi işlevin bildirim ifadesinde kullanılır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="remarks"></a>Açıklamalar  

 Satır içi işlev için bildirim [bildirimi, Function anahtar sözcüğünden](function-entity-sql.md) ve ardından işlev adını temsil eden tanımlayıcıyı (örneğin, "MyAvg") ve ardından parantez içindeki bir parametre tanım listesini (örneğin, "Dues Collection (Decimal)") içerir.  
  
 Parametre tanımı listesi sıfır veya daha fazla parametre tanımından oluşur. Her parametre tanımı, bir tanımlayıcı (örneğin, işlevin parametresinin adı, örneğin, "Dues") ve ardından bir tür tanımı (örneğin, "Collection (Decimal)") oluşur.  
  
 Tür tanımları şunlardan biri olabilir:  
  
- Tanımlayıcının türü (örneğin, "Int32" veya "AdventureWorks. Order").  
  
- Anahtar sözcüğü, `COLLECTION` parantez içinde başka bir tür tanımı tarafından gelir (örneğin, "koleksiyon (AdventureWorks. Order)").  
  
- Anahtar sözcük SATıRı, parantez içindeki Özellik tanımlarının bir listesi gelir (örneğin, "satır (x AdventureWorks. Order)"). Özellik tanımlarının " `identifier type_definition` , `identifier type_definition` ,..." gibi bir biçimi vardır.  
  
- Anahtar sözcük başvurusu, parantez içindeki tanımlayıcının türü tarafından izlenir (örneğin, "ref (AdventureWorks. Order)"). BAŞVURU türü tanımı işleci bağımsız değişken olarak bir varlık türü gerektirir. Bağımsız değişken olarak ilkel bir tür belirtemezsiniz.  
  
 Ayrıca tür tanımlarını iç içe geçirebilirsiniz (örneğin, "koleksiyon (satır (x ref (AdventureWorks. Order))") ").  
  
 Tür tanımı seçenekleri şunlardır:  
  
- `IdentifierName supported_type`veya  
  
- `IdentifierName` KOLEKSIYON ( `type_definition` ) veya  
  
- `IdentifierName` SATıR ( `property_definition` ) veya  
  
- `IdentifierName` REF ( `supported_entity_type` )  
  
 Özellik tanımı seçeneği `IdentifierName type_definition` .  
  
 Desteklenen türler geçerli ad alanındaki türlerdir. Bunlar hem ilkel hem de varlık türlerini içerir.  
  
 Desteklenen varlık türleri yalnızca geçerli ad alanındaki varlık türlerine başvurur. İlkel türler içermez.  
  
## <a name="examples"></a>Örnekler  

 Aşağıda basit tür tanımının bir örneği verilmiştir.  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 Aşağıda, bir koleksıyon türü tanımının bir örneği verilmiştir.  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 Aşağıda satır türü tanımının bir örneği verilmiştir.  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 Aşağıda başvuru türü tanımının bir örneği verilmiştir.  
  
```sql  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
