---
title: Null yapılabilir yapılandırılmış türler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 6b078ae458aba73e82957f84408b1000b216aef9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249807"
---
# <a name="nullable-structured-types-entity-sql"></a>Null yapılabilir yapılandırılmış türler (Entity SQL)
Yapılandırılmış bir türün örneği mevcut olmayan bir örneğidir. `null` Bu, tüm özelliklerde `null` değer bulunan mevcut bir örnekten farklıdır.  
  
 Bu konuda, hangi türlerin null yapılabilir olduğu ve hangi kod desenlerinin `null` yapılandırılmış null yapılabilir türleri örnekleri oluşturulduğu dahil null yapılabilir yapılandırılmış türler açıklanmaktadır.  
  
## <a name="kinds-of-nullable-structured-types"></a>Null yapılabilir yapılandırılmış türler türü  
 Üç tür atanabilir yapı türü vardır:  
  
- Satır türleri.  
  
- Karmaşık türler.  
  
- Varlık türleri.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Yapılandırılmış türlerin null örneklerini üreten kod desenleri  
 Aşağıdaki senaryolar örnekleri üretir `null` :  
  
- Yapılandırılmış `null` bir tür olarak şekillendirme:  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
- Bir temel türün türetilmiş bir tür için yukarı ataması:  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- Yanlış koşula dış birleşim:  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --veya  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --veya  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- `null` Başvurunun başvurusunu kaldırma:  
  
    ```  
    DEREF(NullRef)  
    ```  
  
- Boş bir koleksiyondan ANYELEMENT alma:  
  
    ```  
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
