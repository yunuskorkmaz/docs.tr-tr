---
title: Işlev (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: 4e06b5bf8a2ca62630666ab3e8ba35f0425e3988
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148041"
---
# <a name="function-entity-sql"></a>Işlev (Entity SQL)

Bir Entity SQL sorgu komutunun kapsamındaki bir işlevi tanımlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `function-name`  
 İşlevin adı.  
  
 `parameter-name`  
 İşlevdeki bir parametrenin adı.  
  
 `function_expression`  
 İşlevi olan geçerli bir Entity SQL ifadesi. İşlevindeki komut, `parameter_name` işleve geçirilen parametrelere göre hareket edebilir.  
  
 `data_type`  
 Desteklenen bir türün adı.  
  
 KOLEKSIYON (<type_definition `>` )  
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
  
 Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı tanımlı bir Işlevi çağırma](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).  
  
 İşlevler ayrıca modelin kendisinde de belirtilebilir. Modelde belirtilen işlevler, komutta satır içi olarak belirtilen işlevlerle aynı şekilde yürütülür. Daha fazla bilgi için bkz. [Kullanıcı tanımlı işlevler](user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL komutu `Products` döndürülen ürünlerin filtreleneceği bir tamsayı değeri alan bir işlevi tanımlar.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL komutu, `StringReturnsCollection` döndürülen kişileri filtrelemek için bir dize koleksiyonu alan bir işlevi tanımlar.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL Dili](entity-sql-language.md)
