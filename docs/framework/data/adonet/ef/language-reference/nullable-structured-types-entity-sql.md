---
title: Null yapılabilir yapılandırılmış türler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: b155c672d8c0bef8b01fb26fb49908f094add25a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319480"
---
# <a name="nullable-structured-types-entity-sql"></a>Null yapılabilir yapılandırılmış türler (Entity SQL)
Yapılandırılmış bir türün `null` örneği var olmayan bir örnek. Bu, tüm özelliklerde `null` değerlerine sahip olan mevcut bir örnekten farklıdır.  
  
 Bu konuda, hangi türlerin null yapılabilir olduğu ve hangi kod desenlerinin yapılandırılmış null yapılabilir türler `null` örnekleri ürettiği dahil null yapılabilir yapılandırılmış türler açıklanmaktadır.  
  
## <a name="kinds-of-nullable-structured-types"></a>Null yapılabilir yapılandırılmış türler türü  
 Üç tür atanabilir yapı türü vardır:  
  
- Satır türleri.  
  
- Karmaşık türler.  
  
- Varlık türleri.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Yapılandırılmış türlerin null örneklerini üreten kod desenleri  
 Aşağıdaki senaryolar `null` örnekleri üretir:  
  
- @No__t-0 ' y i yapısal bir tür olarak şekillendirme:  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- Bir temel türün türetilmiş bir tür için yukarı ataması:  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- Yanlış koşula dış birleşim:  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --veya  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --veya  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- @No__t-0 başvurusunun başvurusu:  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- Boş bir koleksiyondan ANYELEMENT alma:  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- Yapılandırılmış türlerin `null` örnekleri denetleniyor:  
  
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

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
