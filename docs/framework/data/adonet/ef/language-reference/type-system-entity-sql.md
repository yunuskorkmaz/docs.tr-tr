---
description: 'Daha fazla bilgi edinin: tür sistemi (Entity SQL)'
title: Tür sistemi (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: 8d0d50a2c82a309a6a496642836aabe23b6bb9bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673394"
---
# <a name="type-system-entity-sql"></a>Tür sistemi (Entity SQL)

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir dizi türü destekler:  
  
- Ve gibi temel (basit) türler `Int32``String.`  
  
- Şemasında tanımlanan,, ve gibi değerler nominal türler <xref:System.Data.Metadata.Edm.EntityType> <xref:System.Data.Metadata.Edm.ComplexType> <xref:System.Data.Metadata.Edm.RelationshipType> .  
  
- Şemada tanımlanmamış anonim türler açıkça: <xref:System.Data.Metadata.Edm.CollectionType> , <xref:System.Data.Metadata.Edm.RowType> , ve <xref:System.Data.Metadata.Edm.RefType> .  
  
 Bu bölümde, şemada açıkça tanımlanmayan ancak Entity SQL tarafından desteklenen anonim türler açıklanmaktadır. İlkel ve nominal türler hakkında bilgi için bkz. [kavramsal model türleri (csdl)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).  
  
## <a name="rows"></a>Satırlar  

 Bir satırın yapısı, yazılan ve satırın içerdiği adlandırılmış üyelerin dizisine bağlıdır. Bir satır türünün kimliği yok ve öğesinden devralınamıyor. Aynı satır türünün örnekleri, Üyeler sırasıyla eşdeğer olduğunda eşdeğerdir. Satırlarda yapısal denklik değerinin ötesinde hiçbir davranış yoktur ve ortak dil çalışma zamanına denk değildir. Sorgular, satırları veya satır koleksiyonlarını içeren yapılara yol açabilir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Sorgular ve ana bilgisayar dili ARASıNDAKI API bağı, sonuçları üreten sorguda satırların nasıl yapıldığını tanımlar. Satır örneği oluşturma hakkında daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.  
  
## <a name="collections"></a>Koleksiyonlar  

 Koleksiyon türleri, diğer nesnelerin sıfır veya daha fazla örneğini temsil eder. Koleksiyon oluşturma hakkında daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.  
  
## <a name="references"></a>Başvurular  

 Başvuru, belirli bir varlık kümesindeki belirli bir varlığa yönelik mantıksal bir işaretçisidir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , başvuruları oluşturmak, oluşturmak ve bunlar arasında gezinmek için aşağıdaki işleçleri destekler:  
  
- [REF](ref-entity-sql.md)  
  
- [CREATEREF](createref-entity-sql.md)  
  
- [ANAHTAR](key-entity-sql.md)  
  
- [DEREF](deref-entity-sql.md)  
  
 Üye erişimi (nokta) işlecini () kullanarak bir başvuruya gidebilirsiniz `.` . Aşağıdaki kod parçacığı, r (Reference) özelliğinde gezinerek ID özelliğini (sıra) ayıklar.  
  
```sql  
select o2.r.Id
from (select ref(o) as r from LOB.Orders as o) as o2
```  
  
 Başvuru değeri null ise veya başvurunun hedefi yoksa sonuç null olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
- [CAST](cast-entity-sql.md)
- [CSDL, SSDL ve MSL Belirtimleri](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
