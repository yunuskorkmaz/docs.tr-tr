---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: f1dd5ba92c7b1eaf7117c9732a78e04e5d5a317a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319450"
---
# <a name="oftype-entity-sql"></a>OFTYPE (Entity SQL)
Belirli türde olan bir sorgu ifadesinden bir nesne koleksiyonu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir nesne koleksiyonu döndüren geçerli bir sorgu ifadesi.  
  
 `test_type`  
 @No__t-0 tarafından döndürülen her bir nesneyi test etmek için tür. Tür bir ad alanı tarafından nitelenmelidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 @No__t-0 türünde bir nesne koleksiyonu veya bir temel tür ya da `test_type` türetilmiş türü. YALNıZCA belirtilmişse, yalnızca `test_type` veya boş bir koleksiyonun örnekleri döndürülür.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 ifadesi, bir koleksiyonun her öğesine karşı bir tür testi gerçekleştirmek için verilen bir tür ifadesini belirtir.  @No__t-0 ifadesi, yalnızca bu tür veya alt türü ile eşdeğer olan öğeleri içeren belirtilen türde yeni bir koleksiyon oluşturur.  
  
 @No__t-0 ifadesi aşağıdaki sorgu ifadesinin kısaltmasıdır:  
  
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
  
 Aşağıdaki tabloda bazı desenler üzerinde `OFTYPE` işlecinin davranışı gösterilmektedir. Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:  
  
|Desen|Davranış|  
|-------------|--------------|  
|OFTYPE (koleksiyon (EntityType), EntityType)|Koleksiyon (EntityType)|  
|OFTYPE (koleksiyon (ComplexType), ComplexType)|Oluşturur|  
|OFTYPE (koleksiyon (RowType), RowType)|Oluşturur|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, bir kurs nesneleri koleksiyonundan Onsitekurs nesnelerinin bir koleksiyonunu döndürmek için OFTYPE işlecini kullanır. Sorgu, [okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.  
  
 [!code-sql[DP EntityServices Concepts#OFTYPE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#oftype)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
