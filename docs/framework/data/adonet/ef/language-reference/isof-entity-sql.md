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
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Türünü belirleyecek geçerli bir sorgu ifadesi.  
  
 BAŞLATıLMADı  
 EDM 'yi geçersiz kılar. ' Nin Boolean sonucu.  
  
 YALNıZCA  
 @No__t-0 ' ın, yalnızca `expression` ' in `type` tipinde olması ve alt türlerinden herhangi biri olmaması durumunda olduğunu belirtir.  
  
 `type`  
 @No__t-0 ' dan test edilecek tür. Tür ad alanı nitelenmiş olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 @no__t `expression`, T türünde ise ve T bir temel tür ya da türetilmiş bir tür `type`; çalışma zamanında `expression` null ise null; Aksi takdirde, @no__t 4.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 ve `expression IS NOT OF (ONLY type)` ifadeleri sırasıyla `NOT (expression IS OF (type))` ve `NOT (expression IS OF (ONLY type))` ile eşdeğerdir.  
  
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
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, bir sorgu ifadesinin türünü tespit etmek için işleç ' i kullanır ve ardından bir nesneyi, bir nesne türünü Onsitekurs türünde bir nesne koleksiyonuna dönüştürmek için DEĞERLENDIR işlecini kullanır. Sorgu, [okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.  
  
 [! Code-SQL [DP EntityServices kavramları # TREAT_ISOF] ~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices kavramları/TSQL/EntitySql. SQL # TREAT_ISOF)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
