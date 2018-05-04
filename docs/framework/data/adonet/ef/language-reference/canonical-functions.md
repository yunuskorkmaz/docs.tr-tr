---
title: Kurallı işlevleri
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: fed6e45056e318ec0bf34951097304ef3c98f629
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="canonical-functions"></a>Kurallı işlevleri
Bu bölümde, tüm veri sağlayıcıları tarafından desteklenir ve tüm sorgulanırken teknolojiler tarafından kullanılan kurallı işlevleri açıklanmaktadır. Kurallı işlevleri bir sağlayıcı tarafından genişletilemez.  
  
 Kurallı bu işlevler sağlayıcı için karşılık gelen bir veri kaynağı işlevi çevrilir. Bu veri kaynakları arasında bir ortak biçiminde ifade işlev çağrılarını sağlar.  
  
 Kurallı bu işlevler veri kaynaklarından bağımsız olduğundan, kurallı işlevleri bağımsız değişkeni ve dönüş türleri kavramsal modelde türleri açısından tanımlanır. Ancak, bazı veri kaynakları, kavramsal modelde tüm türleri desteklemeyebilir.  
  
 Ne zaman kurallı işlevleri kullanıldığı bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, uygun işlevi veri kaynağında çağrılır.  
  
 Null giriş davranış ve hata koşullarını açıkça belirtilen tüm kurallı işlevleri vardır. Depo sağlayıcıları uyumlu bu davranışı olması gerekir, ancak [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] Bu davranış zorlamaz.  
  
 Karşı LINQ senaryoları için sorgular [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] temel alınan veri kaynağında yöntemlerine eşleme CLR yöntemlerini içerir. Kurallı İşlevler, CLR yöntemleri eşlemeye belirli bir yöntemlerini oluşturmak doğru harita, bağımsız olarak veri kaynağı.  
  
## <a name="canonical-functions-namespace"></a>Kurallı işlevleri Namespace  
 Kurallı işlevi için ad alanı <xref:System.Data.Metadata.Edm>. <xref:System.Data.Metadata.Edm> Ad alanındaki tüm sorgular otomatik olarak eklenir. Ancak, başka bir ad alanı içe aktarılırsa kurallı işlevi olarak aynı ada sahip bir işlevi içeren (içinde <xref:System.Data.Metadata.Edm> ad alanı), ad alanı belirtilmelidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Toplu Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 Toplama anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.  
  
 [Kurallı Matematik İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 Matematik anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.  
  
 [Kurallı Dize İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 Dize anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.  
  
 [Kurallı Tarih ve Saat İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 Tarih ve saat anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.  
  
 [Bit Düzeyinde Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 Bit düzeyinde ele [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.  
  
 [Uzamsal İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 Spatial ele [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.  
  
 [Diğer Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 Bit düzeyinde, tarih, dize, matematik veya toplu olarak sınıflandırılan değil işlevleri açıklanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [SQL Server İşlevleri ile Kurallı Kavramsal Model Eşlemesi](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
 [Kullanıcı Tanımlı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
