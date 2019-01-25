---
title: Kurallı İşlevler
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: 4657fd2b68008e4194fc39982dc2ac5b34a644ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513886"
---
# <a name="canonical-functions"></a>Kurallı İşlevler
Bu bölümde, tüm veri sağlayıcıları tarafından desteklenir ve tüm sorgulanırken teknolojiler tarafından kullanılan kurallı işlevler açıklanmaktadır. Kurallı işlevler bir sağlayıcı tarafından genişletilemez.  
  
 Bu kurallı işlevler sağlayıcı için karşılık gelen bir veri kaynağı işlevi çevrilir. Bu işlev çağrılarını veri kaynaklarında yaygın biçiminde ifade sağlar.  
  
 Bu kurallı İşlevler, veri kaynaklarından bağımsız olduğundan, kurallı işlevler bağımsız değişkeni ve dönüş türleri kavramsal model türleri açısından tanımlanır. Ancak, bazı veri kaynakları, kavramsal modelde tüm türleri desteklemeyebilir.  
  
 Ne zaman kurallı işlevler kullanıldığı bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu uygun işlevi veri kaynağında çağrılır.  
  
 Tüm kurallı İşlevler, hem null giriş davranışı hem de açıkça belirtilen hata koşulları vardır. Store sağlayıcıları bu davranışı ile uyumlu olması gerekir ancak [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] bu davranışı zorlamaz.  
  
 LINQ senaryoları için karşı sorgular [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] temel alınan veri kaynağına yöntemlere eşleme CLR yöntemlerini içerir. Kurallı İşlevler, CLR yöntemleri eşlemeye yöntemlerini belirli bir oluşturmak doğru harita, veri kaynağı ne olursa olsun.  
  
## <a name="canonical-functions-namespace"></a>Namespace kurallı İşlevler  
 Ad alanı'kurallı işlevinin <xref:System.Data.Metadata.Edm>. <xref:System.Data.Metadata.Edm> Ad alanı, tüm sorguları otomatik olarak eklenir. Ancak, başka bir ad alanı içe aktarılırsa kurallı işlev ile aynı ada sahip bir işlev içeren (içinde <xref:System.Data.Metadata.Edm> ad alanı), ad alanı belirtilmelidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Toplu Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 Toplama anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevler.  
  
 [Kurallı Matematik İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 Matematik anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevler.  
  
 [Kurallı Dize İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 Dize anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevler.  
  
 [Kurallı Tarih ve Saat İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 Tarih ve saat anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevler.  
  
 [Bit Düzeyinde Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 Bit düzeyinde anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevler.  
  
 [Uzamsal İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 Uzamsal anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevler.  
  
 [Diğer Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 Bit düzeyinde, tarih, dize, matematik veya toplama sınıflandırılan değil işlevleri açıklanır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [SQL Server İşlevleri ile Kurallı Kavramsal Model Eşlemesi](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [Kullanıcı Tanımlı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
