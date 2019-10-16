---
title: Tür tanımları (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 35f660a66fd706b37187056830af5e06ac586caa
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319243"
---
# <a name="type-definitions-entity-sql"></a>Tür tanımları (Entity SQL)
Bir tür tanımı [!INCLUDE[esql](../../../../../../includes/esql-md.md)] satır Içi işlevin bildirim ifadesinde kullanılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Satır içi bir işlev için bildirim [bildirimi, Function anahtar sözcüğünden](function-entity-sql.md) ve ardından işlev adını temsil eden tanımlayıcıyı (örneğin, "MyAvg") ve sonra parantez içindeki bir parametre tanım listesini (örneğin, "Dues koleksiyonu") içerir. Ondalık) ").  
  
 Parametre tanımı listesi sıfır veya daha fazla parametre tanımından oluşur. Her parametre tanımı, bir tanımlayıcı (örneğin, işlevin parametresinin adı, örneğin, "Dues") ve ardından bir tür tanımı (örneğin, "Collection (Decimal)") oluşur.  
  
 Tür tanımları şunlardan biri olabilir:  
  
- Tanımlayıcının türü (örneğin, "Int32" veya "AdventureWorks. Order").  
  
- @No__t-0 anahtar sözcüğü parantez içindeki başka bir tür tanımı tarafından gelir (örneğin, "Collection (AdventureWorks. Order)").  
  
- Anahtar sözcük SATıRı, parantez içindeki Özellik tanımlarının bir listesi gelir (örneğin, "satır (x AdventureWorks. Order)"). Özellik tanımlarının "`identifier type_definition`, `identifier type_definition`,..." gibi bir biçimi vardır.  
  
- Anahtar sözcük başvurusu, parantez içindeki tanımlayıcının türü tarafından izlenir (örneğin, "ref (AdventureWorks. Order)"). BAŞVURU türü tanımı işleci bağımsız değişken olarak bir varlık türü gerektirir. Bağımsız değişken olarak ilkel bir tür belirtemezsiniz.  
  
 Ayrıca tür tanımlarını iç içe geçirebilirsiniz (örneğin, "koleksiyon (satır (x ref (AdventureWorks. Order))") ").  
  
 Tür tanımı seçenekleri şunlardır:  
  
- `IdentifierName supported_type` veya  
  
- `IdentifierName` koleksıyon (`type_definition`) veya  
  
- `IdentifierName` satır (`property_definition`) veya  
  
- `IdentifierName` REF (`supported_entity_type`)  
  
 Özellik tanımı seçeneği `IdentifierName type_definition` ' dır.  
  
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
