---
title: Ad alanları (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7f05067c4bdb859f3661f775c2502852b6658522
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319555"
---
# <a name="namespaces-entity-sql"></a>Ad alanları (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)], tür adları, varlık kümeleri, işlevler gibi genel tanımlayıcılara ad çakışmalarını önlemek için ad alanlarını tanıtır. @No__t-0 ' daki ad alanı desteği, .NET Framework ad alanı desteğiyle benzerdir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], aşağıdaki örnekte gösterildiği gibi, USING yan tümcesinin iki biçimini sağlar: nitelenmiş ad alanları (ad alanı için daha kısa bir diğer ad) ve nitelenmemiş ad alanları.  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Ad çözümleme kuralları  
 Bir tanımlayıcı yerel kapsamlardan çözülemezse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)], Genel kapsamlar (ad alanları) içinde adı bulmaya çalışır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)], önce nitelenmiş ad alanlarından biriyle tanımlayıcı (ön ek) ile eşleştirmeye çalışır. Bir eşleşme varsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] belirtilen ad alanındaki tanımlayıcının geri kalanını çözümlemeye çalışır. Eşleşme bulunmazsa, bir özel durum oluşturulur.  
  
 Sonra, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlayıcı için tüm nitelenmemiş ad alanlarını (giriş durumunda belirtilen) aramaya çalışır. Tanımlayıcı tam olarak bir ad alanında konumlandırılabilir ise, o konum döndürülür. Birden fazla ad alanının bu tanımlayıcı için bir eşleşmesi varsa, bir özel durum oluşturulur. Tanımlayıcı için bir ad alanı tanımlanamıyorsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)], aşağıdaki örnekte gösterildiği gibi, adı bir sonraki dışarı kapsama geçirir (<xref:System.Data.Common.DbCommand> veya <xref:System.Data.Common.DbConnection> nesnesi):  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>.NET Framework farklılıklar  
 .NET Framework kısmen nitelenmiş ad alanlarını kullanabilirsiniz. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] buna izin vermez.  
  
## <a name="adonet-usage"></a>ADO.NET kullanımı  
 Sorgular, ADO.NET <xref:System.Data.Common.DbCommand> nesneleri aracılığıyla ifade edilir. <xref:System.Data.Common.DbCommand> nesneleri <xref:System.Data.Common.DbConnection> nesneler üzerinde oluşturulabilir. Ad alanları <xref:System.Data.Common.DbCommand> ve <xref:System.Data.Common.DbConnection> nesnelerinin bir parçası olarak da belirtilebilir. @No__t-0 sorgunun içindeki bir tanımlayıcıyı çözümleyemezse dış ad alanları araştırılır (benzer kurallara göre).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
