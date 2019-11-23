---
title: IOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: c4c4cbf74cb17cf43e79c42ff42d1e68122fd534
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319713"
---
# <a name="isof-entity-sql"></a>IOF (Entity SQL)
Bir ifadenin türünün belirtilen türde mi yoksa alt türlerinden biri mi olduğunu belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `expression`  
 Türünü belirleyecek geçerli bir sorgu ifadesi.  
  
 DEĞİL  
 EDM 'yi geçersiz kılar. ' Nin Boolean sonucu.  
  
 YALNıZCA  
 ÖĞESININ `true`, yalnızca `expression` tür `type` ve alt türlerinden herhangi biri değilse, döndürdüğünü belirtir.  
  
 `type`  
 `expression` sınanacak tür. Tür ad alanı nitelenmiş olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `expression` T ve T türünde ise `true`, bir temel tür ya da türetilmiş bir tür `type`; çalışma zamanında `expression` null ise null; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 `expression IS NOT OF (type)` ve `expression IS NOT OF (ONLY type)` ifadeleri sırasıyla `NOT (expression IS OF (type))` ve `NOT (expression IS OF (ONLY type))`için sözdizimsel olarak eşdeğerdir.  
  
 Aşağıdaki tabloda, bazı tipik ve köşe desenleri üzerinde `IS OF` işlecinin davranışı gösterilmektedir. Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:  
  
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
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, bir sorgu ifadesinin türünü tespit etmek için işleç ' ı kullanır ve ardından bir nesneyi, bir nesne türünü Onsitekurs türünde bir nesne koleksiyonuna dönüştürmek için DEĞERLENDIR işlecini kullanır. Sorgu, [okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.  
  
 [! Code-SQL [DP EntityServices kavramları # TREAT_ISOF] ~/Samples/Snippets/TSQL/VS_Snippets_Data/DP entityservices kavramları/TSQL/EntitySql. SQL # treat_isof)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
