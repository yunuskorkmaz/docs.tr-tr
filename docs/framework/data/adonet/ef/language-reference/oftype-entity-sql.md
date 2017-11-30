---
title: "OFTYPE (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cd2660eb5fddd0c75b44d0796edce37c83865e81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="oftype-entity-sql"></a>OFTYPE (varlık SQL)
Belirli bir türde bir sorgu ifadesinden nesneler koleksiyonunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Nesneleri topluluğunu döndürür herhangi bir geçerli sorgu ifade.  
  
 `test_type`  
 Türü tarafından döndürülen her nesne test `expression` karşı. Türü bir ad alanı tarafından nitelenmiş olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Türündeki nesneler koleksiyonunu `test_type`, veya bir taban türü veya türetilmiş türü `test_type`. YALNIZCA belirtilen yalnızca örnekler, `test_type` ya da boş bir koleksiyon döndürülür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `OFTYPE` ifadesi her bir koleksiyon öğesinin türü sınaması gerçekleştirmek için verilen bir türü ifade belirtir.  `OFTYPE` İfadesi belirtilen türde ya da olan öğeleri içeren yeni bir koleksiyon oluşturur türü veya alt türünü eşdeğerdir.  
  
 Bir `OFTYPE` ifadesidir aşağıdaki sorgu ifadesi için bir kısaltma:  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Alt çalışan türünün bir yönetici olması koşuluyla, aşağıdaki deyim yalnızca yöneticileri çalışanlar koleksiyonundan koleksiyonu üretir:  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 En fazla türü filtresi kullanılarak bir koleksiyonu cast mümkündür:  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 Tüm Yöneticiler yöneticileri olduğundan, koleksiyon şimdi yöneticileri koleksiyonu olarak belirtilmiş olsa elde edilen koleksiyon hala tüm özgün Yöneticiler içeriyor.  
  
 Aşağıdaki tabloda davranışını gösterilmektedir `OFTYPE` bazı desenleri üzerinden işleci. Sağlayıcı çağrılmadan önce tüm istemci tarafındaki özel durumlar:  
  
|Desen|Davranış|  
|-------------|--------------|  
|OFTYPE(Collection(EntityType), EntityType)|Collection(EntityType)|  
|OFTYPE(Collection(complexType), ComplexType)|Oluşturur|  
|OFTYPE(Collection(RowType), RowType)|Oluşturur|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu OnsiteCourse nesneler koleksiyonunu koleksiyondan Elbette nesneler döndürmeye OFTYPE işleci kullanır. Sorgu dayanır [Okul modeli](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
