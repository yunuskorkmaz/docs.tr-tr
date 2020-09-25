---
title: Ad alanları (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7a53f8e7e70dbc9fa505f7f8619af10a0e44c331
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197813"
---
# <a name="namespaces-entity-sql"></a>Ad alanları (Entity SQL)

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] tür adları, varlık kümeleri, işlevler gibi genel Tanımlayıcılarla ilgili ad çakışmalarını önlemek için ad alanlarını tanıtır. İçindeki ad alanı desteği [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .NET Framework ad alanı desteğine benzerdir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , aşağıdaki örnekte gösterildiği gibi, USING yan tümcesinin iki biçimini sağlar: nitelenmiş ad alanları (ad alanı için daha kısa bir diğer ad) ve nitelenmemiş ad alanları.  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Ad çözümleme kuralları  

 Bir tanımlayıcı yerel kapsamlardan çözülemezse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] adı Genel kapsamlar (ad alanları) içinde bulmaya çalışır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] İlk olarak tanımlayıcı (önek) olarak nitelenmiş ad alanlarından birini eşleştirmeyi dener. Bir eşleşme varsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] belirtilen ad alanındaki tanımlayıcının geri kalanını çözümlemeye çalışır. Eşleşme bulunmazsa, bir özel durum oluşturulur.  
  
 Daha sonra [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tanımlayıcı için tüm nitelenmemiş ad alanlarını (giriş durumunda belirtilen) aramayı dener. Tanımlayıcı tam olarak bir ad alanında konumlandırılabilir ise, o konum döndürülür. Birden fazla ad alanının bu tanımlayıcı için bir eşleşmesi varsa, bir özel durum oluşturulur. Tanımlayıcı için bir ad alanı tanımlanamıyorsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Aşağıdaki örnekte gösterildiği gibi, adı bir sonraki dışarı kapsama ( <xref:System.Data.Common.DbCommand> veya <xref:System.Data.Common.DbConnection> nesne) geçirir:  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>.NET Framework farklılıklar  

 .NET Framework kısmen nitelenmiş ad alanlarını kullanabilirsiniz. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Buna izin vermez.  
  
## <a name="adonet-usage"></a>ADO.NET kullanımı  

 Sorgular ADO.NET nesneleri aracılığıyla ifade edilir <xref:System.Data.Common.DbCommand> . <xref:System.Data.Common.DbCommand> nesneler nesneler üzerinde oluşturulabilir <xref:System.Data.Common.DbConnection> . Ad alanları ve nesnelerinin bir parçası olarak da belirtilebilir <xref:System.Data.Common.DbCommand> <xref:System.Data.Common.DbConnection> . [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Sorgunun içindeki bir tanımlayıcıyı çözümleyemezse dış ad alanları araştırılır (benzer kurallara göre).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
