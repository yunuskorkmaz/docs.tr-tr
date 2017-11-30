---
title: "Ad alanları (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ea5292d20aebdb27da726b0076179fb64631e5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="namespaces-entity-sql"></a>Ad alanları (varlık SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Tür adları, varlık kümeleri, İşlevler vb. gibi genel tanımlayıcıları için ad çakışmalarını önlemek için ad alanları tanıtır. Ad alanı desteği [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ad alanı desteği benzer [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]iki tür yan tümcesi sağlar: tam ad alanları (burada daha kısa bir diğer ad sağlanır ad alanı için) ve nitelenmemiş ad alanları, aşağıdaki örnekte gösterildiği gibi:  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Ad çözümleme kuralları  
 Bir tanımlayıcı yerel kapsamlarda çözümlenemiyorsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] genel kapsamlarda (ad) adı bulmaya çalışır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]İlk tanımlayıcı (önek) eşleşmesi tam ad alanlarından birini ile çalışır. Bir eşleşme varsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] belirtilen ad alanı tanımlayıcıda kalan çözümlemeye çalışır. Eşleşme bulunursa, bir özel durum oluşur.  
  
 Ardından, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (giriş bölümünde belirtilen) tüm nitelenmemiş ad tanımlayıcısı için arama dener. Tanımlayıcı tam olarak bir ad alanında bulunabilir, bu konuma döndürülür. Birden fazla ad alanı bu tanımlayıcı için bir eşleşme varsa, özel durum oluşur. Hiçbir ad alanı için tanımlayıcı, tanımlanabilir varsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] adını sonraki dışa doğru kapsam geçirir ( <xref:System.Data.Common.DbCommand> veya <xref:System.Data.Common.DbConnection> nesnesi) aşağıdaki örnekte gösterildiği gibi:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>.NET Framework arasındaki farklar  
 İçinde [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], kısmen nitelenmiş ad alanlarını kullanabilirsiniz. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Bu izin vermiyor.  
  
## <a name="adonet-usage"></a>ADO.NET kullanımı  
 Sorguları ADO.NET ifade <xref:System.Data.Common.DbCommand> nesneleri. <xref:System.Data.Common.DbCommand>nesneleri üzerinden oluşturulabilen <xref:System.Data.Common.DbConnection> nesneleri. Ad alanları bir parçası olarak da belirtilebilir <xref:System.Data.Common.DbCommand> ve <xref:System.Data.Common.DbConnection> nesneleri. Varsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir tanımlayıcısı çözümlenemiyor sorguyla kendisi, dış ad alanları (benzer kurallar göre) sıklığının.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Varlık SQL genel bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
