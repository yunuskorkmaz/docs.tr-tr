---
title: Null yapılabilir yapılandırılmış türler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: fc2230401ef98c005ab52a845de37482c0dcf698
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202271"
---
# <a name="nullable-structured-types-entity-sql"></a>Null yapılabilir yapılandırılmış türler (Entity SQL)

`null`Yapılandırılmış bir türün örneği mevcut olmayan bir örneğidir. Bu, tüm özelliklerde değer bulunan mevcut bir örnekten farklıdır `null` .  
  
 Bu konuda, hangi türlerin null yapılabilir olduğu ve hangi kod desenlerinin `null` yapılandırılmış null yapılabilir türleri örnekleri oluşturulduğu dahil null yapılabilir yapılandırılmış türler açıklanmaktadır.  
  
## <a name="kinds-of-nullable-structured-types"></a>Null yapılabilir yapılandırılmış türler türü  

 Üç tür atanabilir yapı türü vardır:  
  
- Satır türleri.  
  
- Karmaşık türler.  
  
- Varlık türleri.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Yapılandırılmış türlerin null örneklerini üreten kod desenleri  

 Aşağıdaki senaryolar örnekleri üretir `null` :  
  
- `null`Yapılandırılmış bir tür olarak şekillendirme:  
  
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
  
- Başvurunun başvurusunu kaldırma `null` :  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- Boş bir koleksiyondan ANYELEMENT alma:  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- `null`Yapılandırılmış türlerin örnekleri denetleniyor:  
  
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
