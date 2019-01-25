---
title: Ad alanları (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: eb4b956fa2ac9c0bb68c31d94e15b951807f8108
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724141"
---
# <a name="namespaces-entity-sql"></a>Ad alanları (varlık SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Tür adları, varlık kümelerini, İşlevler ve benzeri gibi genel tanımlayıcı ad çakışmalarını önlemek için ad alanları tanıtır. Ad alanı desteği [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ad alanı desteği benzer [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] İki form USING yan tümcesinin sağlar: tam ad alanları (burada daha kısa bir diğer ad sağlanan ad alanı için) ve nitelenmemiş ad alanları, aşağıdaki örnekte gösterildiği gibi:  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Ad çözümleme kuralları  
 Yerel kapsamlar, tanımlayıcının çözümlenemezse [!INCLUDE[esql](../../../../../../includes/esql-md.md)] adı (ad) genel kapsamlarda bulmaya çalışır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ilk tanımlayıcısı (ön ek) eşleşmesi tam ad alanlarından biri ile çalışır. Bir eşleşme varsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlayıcısının belirtilen ad alanı, kalan çözümlemeye çalışır. Eşleşme bulunursa, bir özel durum oluşturulur.  
  
 Ardından, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (giriş bölümünde belirtilir) tüm nitelenmemiş ad tanımlayıcısı için aranacak çalışır. Tanımlayıcı tam olarak bir ad alanında bulunabilir, bu konuma döndürülür. Birden fazla ad alanı tanımlayıcı için bir eşleşme varsa, bir özel durum oluşturulur. Ad alanı tanımlayıcısı için tanımlanabilir, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sonraki dışa doğru kapsam adını geçirir ( <xref:System.Data.Common.DbCommand> veya <xref:System.Data.Common.DbConnection> nesne) aşağıdaki örnekte gösterildiği gibi:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>.NET Framework arasındaki farklar  
 İçinde [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], kısmen nitelenmiş ad alanları kullanabilirsiniz. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Bu izin vermez.  
  
## <a name="adonet-usage"></a>ADO.NET kullanımı  
 Sorgular ADO.NET ifade <xref:System.Data.Common.DbCommand> nesneleri. <xref:System.Data.Common.DbCommand> nesneler üzerinde oluşturulabilir <xref:System.Data.Common.DbConnection> nesneleri. Ad alanları bir parçası olarak da belirtilebilir <xref:System.Data.Common.DbCommand> ve <xref:System.Data.Common.DbConnection> nesneleri. Varsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir tanımlayıcısı çözümlenemiyor sorgunun kendisi içinde dış ad alanları (benzer kurallar temelinde) araştırıldığı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
