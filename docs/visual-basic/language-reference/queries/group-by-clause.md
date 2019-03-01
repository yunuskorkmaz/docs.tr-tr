---
title: Group By Tümcesi (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 47db8c9dc0562f8eb527eda65bb56404dc1ea8c8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971331"
---
# <a name="group-by-clause-visual-basic"></a>Group By Tümcesi (Visual Basic)
Bir sorgu sonucunun öğelerini gruplandırır. Ayrıca her grup için toplama işlevleri uygulamak için kullanılabilir. Gruplandırma işlemi, bir veya daha fazla anahtarlar üzerinde temel alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Bölümler  
  
-   `listField1`, `listField2`  
  
     İsteğe bağlı. Bir veya daha fazla alan sorgu değişkeni veya açıkça gruplandırılmış sonuca dahil için alanları tanımlayan değişkenleri. Sorgu değişkeni veya değişkenleri tüm alanlar, hiçbir alan belirtilmesi durumunda, gruplandırılmış sonuca dahil edilir.  
  
-   `keyExp1`  
  
     Gerekli. Öğe grupları belirlemek için kullanılacak anahtarı tanımlayan bir ifade. Bir bileşik anahtarı belirtmek için birden fazla anahtar belirtebilir.  
  
-   `keyExp2`  
  
     İsteğe bağlı. İle birlikte bir veya daha fazla ek anahtarlar `keyExp1` bileşik bir anahtar oluşturmak için.  
  
-   `aggregateList`  
  
     Gerekli. Grupların nasıl toplanır tanımlayan bir veya daha fazla ifadeler. Gruplandırılmış sonuçlar için bir üye adını tanımlamak için kullanmak `Group` anahtar sözcüğü aşağıdaki biçimlerden birini olabilir:  
  
    ```  
    Into Group  
    ```  
  
     -veya-  
  
    ```  
    Into <alias> = Group  
    ```  
  
     Gruba uygulanacak toplama işlevleri de içerebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Group By` yan bir sorgunun sonuçlarını gruplarına bölün. Gruplama, bir anahtar veya birden çok anahtarlarını içeren bir bileşik anahtarı temel alır. Eşleşen anahtar değerleri ile ilişkili olan öğeler aynı grupta dahil edilir.  
  
 Kullandığınız `aggregateList` parametresinin `Into` yan tümcesi ve `Group` grubuna başvurmak için kullanılan bir üye adını tanımlamak için anahtar sözcüğü. Toplama işlevi de içerebilir `Into` gruplandırılmış öğeler için değeri hesaplamak için yan tümcesi. Standart toplama işlevleri bir listesi için bkz. [Aggregate tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bulundukları konuma göre (ülke) müşterilerin listesini gruplandırır ve her gruptaki müşterilerin sayısını sağlar. Sonuçları ülke adına göre sıralanır. Gruplandırılmış sonuçlar Şehir adına göre sıralanır.  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By Yan Tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Aggregate Yan Tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Group Join Yan Tümcesi](../../../visual-basic/language-reference/queries/group-join-clause.md)
