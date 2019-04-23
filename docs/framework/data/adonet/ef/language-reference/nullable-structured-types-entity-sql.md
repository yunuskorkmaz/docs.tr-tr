---
title: Boş değer atanabilir yapılandırılmış türler (varlık SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 632b092e1d0d99a2a40cc3cd4b323e234de6232b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127861"
---
# <a name="nullable-structured-types-entity-sql"></a>Boş değer atanabilir yapılandırılmış türler (varlık SQL)
A `null` yapılandırılmış bir tür örneği örneği yok. Bu, tüm özelliklere sahip mevcut bir örneğinden farklı `null` değerleri.  
  
 Bu konuda, hangi türlerin boş değer atanabilir ve ürün hangi kod desenleri gibi boş değer atanabilir yapılandırılmış türler açıklanmaktadır `null` boş değer atanabilir yapılandırılmış türler örnekleri.  
  
## <a name="kinds-of-nullable-structured-types"></a>Tür boş değer atanabilir yapılandırılmış türler  
 Boş değer atanabilir yapı türleri üç tür vardır:  
  
-   Satır türü.  
  
-   Karmaşık türler.  
  
-   Varlık türleri.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Null yapılandırılmış türlerin örneklerini oluşturan kod desenleri  
 Aşağıdaki senaryolarda üretmek `null` örnekleri:  
  
-   Şekillendirme `null` yapılandırılmış bir tür olarak:  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   Türetilmiş bir tür için bir temel türden yukarı çevrim:  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   Dış birleşim koşul false üzerinde:  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --or  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --or  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   Başvuruluyor bir `null` başvurusu:  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   ANYELEMENT öğesinden boş koleksiyon alma:  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   Denetleme `null` yapılandırılmış türleri örnekleri:  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
