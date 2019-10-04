---
title: Işlev (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: bacc773351812a5db60f493f3025c8e4b07dbaa2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833796"
---
# <a name="function-entity-sql"></a>Işlev (Entity SQL)
Bir Entity SQL sorgu komutunun kapsamındaki bir işlevi tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
FUNCTION function-name  
( [ { parameter_name <type_definition>   
        [ ,...n ]  
  ]  
) AS ( function_expression )   
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )   
                | REF ( data_type )   
                | ROW ( row_expression )   
        }   
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `function-name`  
 İşlevin adı.  
  
 `parameter-name`  
 İşlevdeki bir parametrenin adı.  
  
 `function_expression`  
 İşlevi olan geçerli bir Entity SQL ifadesi. İşlevindeki komut, işleve geçirilen `parameter_name` parametreleri üzerinde işlem yapabilir.  
  
 `data_type`  
 Desteklenen bir türün adı.  
  
 KOLEKSIYON (< type_definition @ no__t-0)  
 Desteklenen türlerin, satırların veya başvuruların koleksiyonunu döndüren bir ifade.  
  
 REF **(** `data_type` **)**  
 Bir varlık türüne başvuru döndüren bir ifade.  
  
 SATıR **(** `row_expression` **)**  
 Bir veya daha fazla değerden adsız, yapısal olarak yazılmış kayıtlar döndüren bir ifade. Daha fazla bilgi için bkz. [satır](row-entity-sql.md).  
  
## <a name="remarks"></a>Açıklamalar  
 İşlev imzaları farklı olduğu sürece, aynı ada sahip birden çok işlev satır içi olarak bildirilemez. Daha fazla bilgi için bkz. [Işlev aşırı yükleme çözünürlüğü](function-overload-resolution-entity-sql.md).  
  
 Satır içi bir işlev, bir Entity SQL komutunda, yalnızca bu komutta tanımlandıktan sonra çağrılabilir. Ancak, satır içi bir işlev başka bir satır içi işlevin içinde, çağrılan işlev tanımlanmadan önce veya sonra çağrılabilir. Aşağıdaki örnekte, B işlevi tanımlanmadan önce bir çağrı işlevi B işlevini işle:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı tanımlı bir Işlevi çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).  
  
 İşlevler ayrıca modelin kendisinde de belirtilebilir. Modelde belirtilen işlevler, komutta satır içi olarak belirtilen işlevlerle aynı şekilde yürütülür. Daha fazla bilgi için bkz. [Kullanıcı tanımlı işlevler](user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL komutu, döndürülen ürünlerin filtreleneceği bir tamsayı değeri alan `Products` işlevini tanımlar.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL komutu, döndürülen kişileri filtrelemek için bir dize koleksiyonu alan `StringReturnsCollection` işlevini tanımlar.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL başvurusu](entity-sql-reference.md)
- [Entity SQL dili](entity-sql-language.md)
