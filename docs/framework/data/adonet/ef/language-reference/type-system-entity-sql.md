---
title: "Tür sistemi (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e6eea471aa421cf5a154e6873c7ea64b71733bfd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="type-system-entity-sql"></a>Tür sistemi (varlık SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]bir dizi türlerini destekler:  
  
-   Primitive (Basit) türleri gibi `Int32` ve`String.`  
  
-   Şemada tanımlanan gibi nominal türleri <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, ve <xref:System.Data.Metadata.Edm.RelationshipType>.  
  
-   Şemada açıkça tanımlanmayan anonim türler: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, ve <xref:System.Data.Metadata.Edm.RefType>.  
  
 Bu bölümde yer alan şemada açıkça tanımlanmayan ancak tarafından desteklenen anonim türleri açıklanmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Basit ve nominal türleri hakkında daha fazla bilgi için bkz: [kavramsal Model türü (CSDL)](http://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4).  
  
## <a name="rows"></a>Satırları  
 Bir satır yapısını satır oluşan yazılan ve adlandırılmış üyeleri bir dizi bağlıdır. Satır türü yok kimliği vardır ve kaynağından devralındı olamaz. Aynı satır türü örnekleri sırasıyla eşdeğer üyeleriyse eşdeğerdir. Satırları kendi yapısal eşdeğer ötesinde davranışı yok ve ortak dil çalışma zamanı'nda eşdeğeri sahiptir. Sorgu satırları veya satır koleksiyonları içeren yapılarını neden olabilir. API bağlama arasında [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular ve ana bilgisayar dil tanımlar satırları sonuç getirdi sorguda nasıl gerçekleştirilirler. Bir satır örneği oluşturma hakkında daha fazla bilgi için bkz: [oluşturma türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="collections"></a>Koleksiyonlar  
 Koleksiyon türleri diğer nesneleri sıfır veya daha fazla örneğini temsil eder. Koleksiyon oluşturma hakkında daha fazla bilgi için bkz: [oluşturma türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="references"></a>Referanslar  
 Bir başvuru, belirli bir varlık kümesinde belirli bir varlık için mantıksal bir işaretçidir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]oluşturun, deconstruct ve başvurular arasında gezinmek için aşağıdaki işleçleri destekler:  
  
-   [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
-   [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
-   [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
-   [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 Üye erişim (nokta) işlecini kullanarak bir başvuru gezinebilirsiniz (`.`). Aşağıdaki kod parçacığında, r (başvuru) özelliği üzerinden giderek kimliği özelliği (sırası) ayıklar.  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 Başvuru değer null ise veya başvuru hedef için yoksa sonuç NULL'dur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)  
 [CSDL, SSDL ve MSL Belirtimleri](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
