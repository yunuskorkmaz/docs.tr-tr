---
title: "Kurallı işlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1f676c88691f0ba80ca682d720adf649ab612cfb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
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
