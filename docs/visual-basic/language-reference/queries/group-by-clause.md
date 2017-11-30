---
title: "Group By Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b719bfa2ebe4c324acf82a03e215e481283845fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="group-by-clause-visual-basic"></a>Group By Tümcesi (Visual Basic)
Sorgu sonucu öğelerini gruplandırır. Ayrıca her gruba toplama işlevleri uygulamak için kullanılabilir. Gruplandırma işlemi bir veya daha fazla anahtarları temel alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Bölümler  
  
-   `listField1`, `listField2`  
  
     İsteğe bağlı. Bir veya daha fazla alanlar sorgu değişkeni veya açıkça gruplandırılmış sonucu dahil edilecek alanları tanımlayın değişkenleri. Hiçbir alan belirtilmedi, tüm alanlar sorgu değişkeni veya değişkenleri gruplandırılmış sonucu dahil edilir.  
  
-   `keyExp1`  
  
     Gerekli. Öğe gruplarını belirlemek için kullanılacak anahtarı tanımlayan bir ifade. Bir bileşik anahtarı belirtmek için birden fazla anahtar belirtebilirsiniz.  
  
-   `keyExp2`  
  
     İsteğe bağlı. İle birlikte bir veya daha fazla ek anahtarlar `keyExp1` bileşik bir anahtar oluşturmak için.  
  
-   `aggregateList`  
  
     Gerekli. Grupları nasıl toplanır tanımlayan bir veya daha fazla ifade. Gruplandırılmış sonuçlar için bir üye adı tanımlamak için kullanmak `Group` anahtar sözcüğünü aşağıdaki biçimlerden birini olabilir:  
  
    ```  
    Into Group  
    ```  
  
     veya  
  
    ```  
    Into <alias> = Group  
    ```  
  
     Gruba uygulamak için toplama işlevleri de içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Group By` yan tümcesini bir sorgunun sonuçlarını gruplarına bölün. Gruplandırma bir anahtar veya birden çok anahtarları oluşan bir bileşik anahtarı temel alan. Eşleşen anahtar değerleri ile ilişkili öğeleri aynı grupta dahil edilir.  
  
 Kullandığınız `aggregateList` parametresinin `Into` yan tümcesi ve `Group` grubuna başvurmak için kullanılan üye adı tanımlamak için anahtar sözcüğü. Toplama işlevleri içinde dahil edebilirsiniz `Into` gruplandırılmış öğeler için değerleri hesaplamak için yan tümcesi. Standart toplama işlevleri bir listesi için bkz: [Aggregate tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde konumuna (ülke) bağlı müşteri listesi grupları ve her grubundaki müşterilerin sayısını sağlar. Sonuçları ülke adına göre sıralanır. Gruplandırılmış sonuçları Şehir adına göre sıralanır.  
  
 [!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorguları](../../../visual-basic/language-reference/queries/queries.md)  
 [Select tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From yan tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [AGGREGATE tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Group Join tümcesi](../../../visual-basic/language-reference/queries/group-join-clause.md)
