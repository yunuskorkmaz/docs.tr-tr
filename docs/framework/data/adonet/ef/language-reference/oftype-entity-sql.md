---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: 375fe9ce52ae290c175e42276b6b526766f6699c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547518"
---
# <a name="oftype-entity-sql"></a>OFTYPE (Entity SQL)
Belirli türde olan bir sorgu ifadesinden bir nesne koleksiyonu döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 `expression`  
 Bir nesne koleksiyonu döndüren geçerli bir sorgu ifadesi.  
  
 `test_type`  
 Tarafından döndürülen her nesnenin test edilecek tür `expression` . Tür bir ad alanı tarafından nitelenmelidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Türünde bir nesne koleksiyonu `test_type` veya temel tür ya da türetilmiş tür `test_type` . YALNıZCA belirtilmişse, yalnızca `test_type` veya boş bir koleksiyonun örnekleri döndürülür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `OFTYPE` ifade, bir koleksiyonun her öğesine karşı bir tür testi gerçekleştirmek için verilen bir tür ifadesini belirtir.  `OFTYPE`İfade, yalnızca bu tür veya alt türü ile eşdeğer olan öğeleri içeren belirtilen türde yeni bir koleksiyon oluşturur.  
  
 `OFTYPE`İfade aşağıdaki sorgu ifadesinin kısaltmasıdır:  
  
```sql  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Bir yöneticinin çalışan bir alt türü olduğu için, aşağıdaki ifade bir çalışan koleksiyonundan yalnızca Yöneticiler koleksiyonu oluşturur:  
  
```sql  
OfType(employees, NamespaceName.Manager)  
```  
  
 Tür filtresi kullanılarak bir koleksiyon atama de mümkündür:  
  
```sql
OfType(executives, NamespaceName.Manager)  
```  
  
 Tüm Yöneticiler yöneticilerden dolayı, sonuçta elde edilen koleksiyon tüm özgün yöneticileri içerir, ancak koleksiyon artık bir Yöneticiler koleksiyonu olarak türdedir.  
  
 Aşağıdaki tablo, `OFTYPE` bazı desenlerdeki işlecin davranışını gösterir. Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:  
  
|Desen|Davranış|  
|-------------|--------------|  
|OFTYPE (koleksiyon (EntityType), EntityType)|Koleksiyon (EntityType)|  
|OFTYPE (koleksiyon (ComplexType), ComplexType)|Oluşturur|  
|OFTYPE (koleksiyon (RowType), RowType)|Oluşturur|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir kurs nesneleri koleksiyonundan Onsitekurs nesnelerinin bir koleksiyonunu döndürmek IÇIN OFTYPE işlecini kullanır. Sorgu, [okul modelini](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.  
  
 [!code-sql[DP EntityServices Concepts#OFTYPE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#oftype)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
