---
title: Ad alanları (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 395ffb23859be27b4897dfc352f6e44d52286b26
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249988"
---
# <a name="namespaces-entity-sql"></a>Ad alanları (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]tür adları, varlık kümeleri, işlevler gibi genel Tanımlayıcılarla ilgili ad çakışmalarını önlemek için ad alanlarını tanıtır. İçindeki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ad alanı desteği .NET Framework ad alanı desteğine benzerdir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], aşağıdaki örnekte gösterildiği gibi, USING yan tümcesinin iki biçimini sağlar: nitelenmiş ad alanları (ad alanı için daha kısa bir diğer ad) ve nitelenmemiş ad alanları.  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Ad çözümleme kuralları  
 Bir tanımlayıcı yerel kapsamlardan çözülemezse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] adı Genel kapsamlar (ad alanları) içinde bulmaya çalışır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]İlk olarak tanımlayıcı (önek) olarak nitelenmiş ad alanlarından birini eşleştirmeyi dener. Bir eşleşme varsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] belirtilen ad alanındaki tanımlayıcının geri kalanını çözümlemeye çalışır. Eşleşme bulunmazsa, bir özel durum oluşturulur.  
  
 Daha sonra tanımlayıcı için tüm nitelenmemiş ad alanlarını (giriş durumunda belirtilen) aramayı dener.[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Tanımlayıcı tam olarak bir ad alanında konumlandırılabilir ise, o konum döndürülür. Birden fazla ad alanının bu tanımlayıcı için bir eşleşmesi varsa, bir özel durum oluşturulur. Tanımlayıcı için bir ad alanı tanımlanamıyorsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aşağıdaki örnekte gösterildiği gibi, adı bir sonraki dışarı kapsama <xref:System.Data.Common.DbCommand> (veya <xref:System.Data.Common.DbConnection> nesne) geçirir:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>.NET Framework farklılıklar  
 .NET Framework kısmen nitelenmiş ad alanlarını kullanabilirsiniz. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Buna izin vermez.  
  
## <a name="adonet-usage"></a>ADO.NET kullanımı  
 Sorgular ADO.net <xref:System.Data.Common.DbCommand> nesneleri aracılığıyla ifade edilir. <xref:System.Data.Common.DbCommand>nesneler nesneler üzerinde <xref:System.Data.Common.DbConnection> oluşturulabilir. Ad alanları <xref:System.Data.Common.DbCommand> ve <xref:System.Data.Common.DbConnection> nesnelerinin bir parçası olarak da belirtilebilir. Sorgunun içindeki bir tanımlayıcıyı çözümleyemezsedışadalanlarıaraştırılır(benzerkurallaragöre).[!INCLUDE[esql](../../../../../../includes/esql-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
