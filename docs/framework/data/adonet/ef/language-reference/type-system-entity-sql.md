---
title: Tip Sistemi (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: b8b721aff5b7886fdb897ecaa3dcc163ec94ae79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149837"
---
# <a name="type-system-entity-sql"></a>Tip Sistemi (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]bir dizi türü destekler:  
  
- Gibi ilkel (basit) `Int32` türleri ve`String.`  
  
- Şemada tanımlanan nominal türleri, gibi <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, <xref:System.Data.Metadata.Edm.RelationshipType>ve .  
  
- Şemada açıkça tanımlanmayan anonim türler: <xref:System.Data.Metadata.Edm.CollectionType> <xref:System.Data.Metadata.Edm.RowType>, <xref:System.Data.Metadata.Edm.RefType>, ve .  
  
 Bu bölümde, şemada açıkça tanımlanmayan ancak Entity SQL tarafından desteklenen anonim türleri açıklanmaktadır. İlkel ve nominal türler hakkında bilgi için [Kavramsal Model Türleri (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)bakın.  
  
## <a name="rows"></a>Satırlar  
 Bir satırın yapısı, satırın oluştuğu yazılan ve adlandırılmış üyelerin sıralarına bağlıdır. Satır türü hiçbir kimliği vardır ve devralınamaz. Üyeler sırasıyla eşdeğerse, aynı satır türündeki örnekler eşdeğerdir. Satırların yapısal eşdeğerliklerinin ötesinde hiçbir davranışı yoktur ve ortak dil çalışma zamanında eşdeğeri yoktur. Sorgular satır veya satır koleksiyonları içeren yapılarneden olabilir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Sorgular ve ana bilgisayar dili arasındaki API bağlama, sonucu oluşturan sorguda satırların nasıl gerçekleştirildiğini tanımlar. Satır örneğinin nasıl oluşturulabildiğini öğrenmek için [bkz.](constructing-types-entity-sql.md)  
  
## <a name="collections"></a>Koleksiyonlar  
 Koleksiyon türleri diğer nesnelerin sıfır veya daha fazla örneğini temsil eder. Koleksiyonun nasıl oluşturulabildiğini öğrenmek için [bkz.](constructing-types-entity-sql.md)  
  
## <a name="references"></a>Başvurular  
 Başvuru, belirli bir varlık kümesindeki belirli bir varlığa mantıksal işaretçidir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]aşağıdaki işleçleri başvurular oluşturmak, yapısızlaştırılması ve gezinmek için destekler:  
  
- [REF](ref-entity-sql.md)  
  
- [CREATEREF](createref-entity-sql.md)  
  
- [Anahtar](key-entity-sql.md)  
  
- [DEREF](deref-entity-sql.md)  
  
 Üye erişim (nokta)`.`işleci(nokta) operatörlerini kullanarak referans ta gezinebilirsiniz. Aşağıdaki parçacık, r (reference) özelliğinde gezinerek Id özelliğini (Siparişin) ayıklar.  
  
```sql  
select o2.r.Id
from (select ref(o) as r from LOB.Orders as o) as o2
```  
  
 Başvuru değeri null ise veya başvurunun hedefi yoksa, sonuç null'dur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
- [CAST](cast-entity-sql.md)
- [CSDL, SSDL ve MSL Belirtimleri](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
