---
title: "Boş değer atanabilir yapılandırılmış türler (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 29b0aa7f6f155de2c55f88b4c796ecc482d1cb84
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="nullable-structured-types-entity-sql"></a>Boş değer atanabilir yapılandırılmış türler (varlık SQL)
A `null` yapılandırılmış bir tür örneği olan mevcut bir örneği. Bu, tüm özellikleri olan mevcut örneğinden farklı değildir `null` değerleri.  
  
 Bu konuda, hangi tür boş değer atanabilir ve ürün hangi kod düzenleri dahil olmak üzere boş değer atanabilir yapılandırılmış türler açıklanmaktadır `null` yapılandırılmış boş değer atanabilir türler örnekleri.  
  
## <a name="kinds-of-nullable-structured-types"></a>Boş değer atanabilir yapılandırılmış türleri tür  
 Üç tür boş değer atanabilir yapı türleri şunlardır:  
  
-   Satır türleri.  
  
-   Karmaşık türler.  
  
-   Varlık türü.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Yapılandırılmış türlerin Null örnekleri oluşturan kod düzenleri  
 Aşağıdaki senaryolarda üretmek `null` örnekleri:  
  
-   Şekillendirme `null` yapılandırılmış bir tür olarak:  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   Üst türe çevirme türetilmiş bir tür için taban türü:  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   Dış birleşim false koşulunu:  
  
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
  
-   Başvurusunun kaldırılmasının bir `null` başvurusu:  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   ANYELEMENT öğesinden boş koleksiyon alma:  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   Denetleme `null` yapılandırılmış türlerin örnekleri:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
