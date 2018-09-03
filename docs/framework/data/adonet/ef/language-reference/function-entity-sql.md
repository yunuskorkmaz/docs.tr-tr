---
title: İŞLEV (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: 1c02583400f9092dcb5008239bfd1fd73c63c326
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485553"
---
# <a name="function-entity-sql"></a>İŞLEV (varlık SQL)
Bir işlev bir varlık SQL sorgusu komutu kapsamında tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
  
## <a name="arguments"></a>Arguments  
 `function-name`  
 İşlevin adı.  
  
 `parameter-name`  
 İşlev bir parametre adı.  
  
 `function_expression`  
 İşlev, geçerli bir varlık SQL ifadesi. Komut içinde işlev üzerinde işlem yapabileceğiniz `parameter_name` işleve geçirilen parametreler.  
  
 `data_type`  
 Desteklenen bir tür adı.  
  
 KOLEKSİYON (< type_definition`>` )  
 Desteklenen türler, satır veya başvuruları koleksiyonunu döndüren bir ifade.  
  
 REF **(**`data_type`**)**  
 Bir varlık türü referansı döndüren bir ifade.  
  
 SATIR **(**`row_expression`**)**  
 Anonim, döndüren bir ifade, yapısal olarak bir veya daha fazla değer kayıtlardan yazdınız. Daha fazla bilgi için [satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="remarks"></a>Açıklamalar  
 İşlev imzası farklı olduğu sürece, aynı ada sahip birden çok işlev satır içi olarak bildirilebilir. Daha fazla bilgi için [işlev aşırı yükleme çözünürlüğü](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
 Bu komutta yalnızca tanımlandıktan sonra bir satır içi işlevi bir varlık SQL komutunu çağrılabilir. Ancak, satır içi işlev önce ya da çağrılan işlevi tanımlandıktan sonra başka bir satır içi işlev içinde çağrılabilir. B işlevi tanımlanmadan önce aşağıdaki örnekte, B işlevi bir çağrıları işlev:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Daha fazla bilgi için [nasıl yapılır: bir kullanıcı tanımlı işlevi çağırma](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02).  
  
 İşlevler Ayrıca model içinde bildirilebilir. Model içinde bildirilen işlevlerle aynı şekilde komutta bildirilen satır içi işlevleri gibi yürütülür. Daha fazla bilgi için [kullanıcı tanımlı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL komutunu bir işlevi tanımlayan `Products` döndürülen ürünleri filtrelemek için bir tamsayı değeri alır.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL komutunu bir işlevi tanımlayan `StringReturnsCollection` döndürülen kişiler filtrelemek için dizeleri koleksiyonunu alır.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity SQL Dili](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
