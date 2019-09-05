---
title: IOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 3b746a82f72fc7f42f9d91ddd0a7d6f4f86ac0bb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250571"
---
# <a name="isof-entity-sql"></a>IOF (Entity SQL)
Bir ifadenin türünün belirtilen türde mi yoksa alt türlerinden biri mi olduğunu belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Türünü belirleyecek geçerli bir sorgu ifadesi.  
  
 DEĞİL  
 EDM 'yi geçersiz kılar. ' Nin Boolean sonucu.  
  
 YALNIZCA  
 Öğesinin `true` yalnızcatürü`type` ise ve alt türlerinden herhangi biri değilse, bu döndürdüğünü belirtir. `expression`  
  
 `type`  
 Sınanacak `expression` tür. Tür ad alanı nitelenmiş olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`Eğer `expression` t ve t türünde ise, bir temel tür ya da türetilmiş bir `type`tür; çalışma zamanında null ise null `expression` ; Aksi durumda, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 İfadeler `expression IS NOT OF (type)` ve `expression IS NOT OF (ONLY type)` sırasıyla `NOT (expression IS OF (type))` ve ile`NOT (expression IS OF (ONLY type))`aynıdır.  
  
 Aşağıdaki tabloda, bazı tipik ve köşe `IS OF` desenlerinde işlecin davranışı gösterilmektedir. Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:  
  
|Desen|Davranış|  
|-------------|--------------|  
|null (EntityType)|Oluşturur|  
|null (ComplexType)|Oluşturur|  
|null (RowType)|Oluşturur|  
|DAVRAN (EntityType olarak null), (EntityType)|DBNull döndürür|  
|DAVRAN (ComplexType olarak null), (ComplexType)|Oluşturur|  
|DEĞERLENDIR (RowType olarak null), (RowType)|Oluşturur|  
|EntityType (EntityType)|True/false döndürür|  
|ComplexType (ComplexType)|Oluşturur|  
|RowType, (RowType)|Oluşturur|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir sorgu ifadesinin türünü tespit etmek için işleç ' i kullanır ve sonra bir nesne türünü, onsitekurs türünde bir nesne koleksiyonuna dönüştürmek için değerlendir işlecini kullanır. Sorgu, [okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
