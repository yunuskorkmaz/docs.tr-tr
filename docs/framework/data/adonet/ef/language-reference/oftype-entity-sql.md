---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: 36701a5e75e804ea541d242aaff243de0b24cec3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249790"
---
# <a name="oftype-entity-sql"></a>OFTYPE (Entity SQL)
Belirli türde olan bir sorgu ifadesinden bir nesne koleksiyonu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir nesne koleksiyonu döndüren geçerli bir sorgu ifadesi.  
  
 `test_type`  
 Tarafından `expression` döndürülen her nesnenin test edilecek tür. Tür bir ad alanı tarafından nitelenmelidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Türünde `test_type`bir nesne koleksiyonu veya temel tür ya da türetilmiş `test_type`tür. Yalnızca belirtilmişse, yalnızca `test_type` veya boş bir koleksiyonun örnekleri döndürülür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `OFTYPE` ifade, bir koleksiyonun her öğesine karşı bir tür testi gerçekleştirmek için verilen bir tür ifadesini belirtir.  İfade `OFTYPE` , yalnızca bu tür veya alt türü ile eşdeğer olan öğeleri içeren belirtilen türde yeni bir koleksiyon oluşturur.  
  
 `OFTYPE` İfade aşağıdaki sorgu ifadesinin kısaltmasıdır:  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Bir yöneticinin çalışan bir alt türü olduğu için, aşağıdaki ifade bir çalışan koleksiyonundan yalnızca Yöneticiler koleksiyonu oluşturur:  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 Tür filtresi kullanılarak bir koleksiyon atama de mümkündür:  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 Tüm Yöneticiler yöneticilerden dolayı, sonuçta elde edilen koleksiyon tüm özgün yöneticileri içerir, ancak koleksiyon artık bir Yöneticiler koleksiyonu olarak türdedir.  
  
 Aşağıdaki tablo, bazı desenlerdeki `OFTYPE` işlecin davranışını gösterir. Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:  
  
|Desen|Davranış|  
|-------------|--------------|  
|OFTYPE (koleksiyon (EntityType), EntityType)|Koleksiyon (EntityType)|  
|OFTYPE (koleksiyon (ComplexType), ComplexType)|Oluşturur|  
|OFTYPE (koleksiyon (RowType), RowType)|Oluşturur|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir kurs nesneleri koleksiyonundan onsitekurs nesnelerinin bir koleksiyonunu döndürmek için OFTYPE işlecini kullanır. Sorgu, [okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
