---
title: İşLEV (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: fd7f484733e7135d2d6c8094b6527d672a988088
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150304"
---
# <a name="function-entity-sql"></a>İşLEV (Entity SQL)
Varlık SQL sorgu komutu kapsamındaki bir işlevi tanımlar.  
  
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
 Fonksiyonun adı.  
  
 `parameter-name`  
 İşlevdeki bir parametrenin adı.  
  
 `function_expression`  
 İşlev olan geçerli bir Entity SQL ifadesi. İşlevdeki komut, işleve geçirilen parametrelere göre `parameter_name` hareket edebilir.  
  
 `data_type`  
 Desteklenen bir türün adı.  
  
 TOPLAMA (`>` <type_definition )  
 Desteklenen türler, satırlar veya başvurular koleksiyonunu döndüren bir ifade.  
  
 REF **(**`data_type`**)**  
 Bir varlık türüne başvuru döndüren bir ifade.  
  
 SATıR **(**`row_expression`**)**  
 Bir veya daha fazla değerden anonim, yapısal olarak yazılan kayıtları döndüren bir ifade. Daha fazla bilgi için [ROW'a](row-entity-sql.md)bakın.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlev imzaları farklı olduğu sürece, aynı ada sahip birden çok işlev satır içinde bildirilebilir. Daha fazla bilgi için [bkz.](function-overload-resolution-entity-sql.md)  
  
 Bir satır arası işlev, varlık SQL komutunda ancak bu komutta tanımlandıktan sonra çağrılabilir. Ancak, bir satır içi işlev, çağrılan işlev tanımlandıktan önce veya sonra başka bir satır içi işlevin içinde çağrılabilir. Aşağıdaki örnekte, B işlevi tanımlanmadan önce A işlevi B'yi çağırır:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Daha fazla bilgi için [bkz: Kullanıcı Tanımlı İşlev'i çağırın.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 İşlevler modelin kendisinde de bildirilebilir. Modelde bildirilen işlevler, komutta satır içinde bildirilen işlevler gibi yürütülür. Daha fazla bilgi için [Bkz. Kullanıcı Tanımlı Fonksiyonlar.](user-defined-functions-entity-sql.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL komutu, `Products` döndürülen ürünleri filtrelemek için tamsayı değeri alan bir işlev tanımlar.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL komutu, `StringReturnsCollection` döndürülen kişileri filtrelemek için dize ler koleksiyonu alan bir işlev tanımlar.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL Dili](entity-sql-language.md)
