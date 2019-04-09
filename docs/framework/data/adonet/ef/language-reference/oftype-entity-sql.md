---
title: OFTYPE (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: bbc3ffd4902fe8c1c41aebe88317d0e3c32f7771
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077101"
---
# <a name="oftype-entity-sql"></a>OFTYPE (varlık SQL)
Belirli bir tür bir sorgu ifadesinden nesnelerinin bir koleksiyonunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Nesnelerin bir koleksiyonunu döndürür herhangi bir geçerli ifade.  
  
 `test_type`  
 Tarafından döndürülen her nesne sınanacak tür `expression` karşı. Türü bir ad alanı tarafından nitelendirilmelidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Türündeki nesneler koleksiyonunu `test_type`, veya bir temel tür veya türetilmiş bir tür `test_type`. YALNIZCA belirtilen yalnızca örnekler, `test_type` ya da boş bir koleksiyon döndürülür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `OFTYPE` koleksiyonun her öğesine karşı bir tür testi gerçekleştirmek için verilen bir tür ifadesi ifade belirtir.  `OFTYPE` İfade ya da olan öğeleri içeren belirtilen türe ait yeni bir koleksiyon oluşturur, tür veya alt türünü eşdeğerdir.  
  
 Bir `OFTYPE` aşağıdaki sorgu ifadesinin bir kısaltma ifadesidir:  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Çalışan bir alt yöneticisidir düşünüldüğünde, aşağıdaki ifade yalnızca çalışanlar koleksiyonu yöneticileri koleksiyonu oluşturur:  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 En fazla türü filtresi kullanarak koleksiyon türüne mümkündür:  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 Tüm Yöneticiler yöneticileri olduğundan, koleksiyon artık yöneticileri koleksiyonu olarak yazılmış olsa, elde edilen koleksiyon hala tüm özgün Yöneticiler içeriyor.  
  
 Aşağıdaki tabloda davranışını gösteren `OFTYPE` bazı desenleri üzerinden işleci. Sağlayıcı çağrılmadan önce tüm istemci tarafında özel durumlar:  
  
|Desen|Davranış|  
|-------------|--------------|  
|OFTYPE(Collection(EntityType), EntityType)|Collection(EntityType)|  
|OFTYPE(Collection(complexType), ComplexType)|Oluşturur|  
|OFTYPE(Collection(RowType), RowType)|Oluşturur|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu OnsiteCourse nesnelerden oluşan bir koleksiyon bir koleksiyondan Elbette nesneler döndürmeye OFTYPE işleci kullanır. Sorgu dayanır [Okul modeli](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
