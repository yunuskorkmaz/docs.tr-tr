---
title: IOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 3cbbc9b6feda1bde104ed2c95d4dca274b090028
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202285"
---
# <a name="isof-entity-sql"></a>IOF (Entity SQL)

Bir ifadenin türünün belirtilen türde mi yoksa alt türlerinden biri mi olduğunu belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Türünü belirleyecek geçerli bir sorgu ifadesi.  
  
 NOT  
 EDM 'yi geçersiz kılar. ' Nin Boolean sonucu.  
  
 YALNıZCA  
 ÖĞESININ `true` yalnızca `expression` türü ise `type` ve alt türlerinden HERHANGI biri değilse, bu döndürdüğünü belirtir.  
  
 `type`  
 Sınanacak tür `expression` . Tür ad alanı nitelenmiş olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `true` Eğer `expression` t ve t türünde ise, bir temel tür ya da türetilmiş bir tür `type` ; `expression` çalışma zamanında null ise null; Aksi durumda, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 İfadeler `expression IS NOT OF (type)` ve `expression IS NOT OF (ONLY type)` `NOT (expression IS OF (type))` sırasıyla ve ile aynıdır `NOT (expression IS OF (ONLY type))` .  
  
 Aşağıdaki tabloda, `IS OF` bazı tipik ve köşe desenlerinde işlecin davranışı gösterilmektedir. Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:  
  
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

 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir sorgu ifadesinin türünü tespit etmek için işleç ' i kullanır ve sonra bir nesne türünü, Onsitekurs türünde bir nesne koleksiyonuna dönüştürmek IÇIN değerlendir işlecini kullanır. Sorgu, [okul modelini](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.  
  
 [! Code-SQL [DP EntityServices kavramları # TREAT_ISOF] ~/Samples/Snippets/TSQL/VS_Snippets_Data/DP entityservices kavramları/TSQL/EntitySql. SQL # treat_isof)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
