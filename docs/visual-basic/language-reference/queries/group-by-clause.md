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
ms.openlocfilehash: 8b3a480c226debc529c268e83437d15192592bd3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004761"
---
# <a name="group-by-clause-visual-basic"></a>Group By Tümcesi (Visual Basic)
Bir sorgu sonucunun öğelerini gruplandırır. , Her gruba toplam işlevleri uygulamak için de kullanılabilir. Gruplandırma işlemi bir veya daha fazla anahtara göre belirlenir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Bölümler  
  
- `listField1`, `listField2`  
  
     İsteğe bağlı. Gruplanmış sonuca dahil edilecek alanları açıkça tanımlayan sorgu değişkeninin veya değişkenlerinin bir veya daha fazla alanı. Hiçbir alan belirtilmemişse, sorgu değişkeni veya değişkenlerinin tüm alanları gruplanmış sonuca dahil edilir.  
  
- `keyExp1`  
  
     Gerekli. Öğe gruplarını belirlemekte kullanılacak anahtarı tanımlayan bir ifade. Bileşik bir anahtar belirtmek için birden fazla anahtar belirtebilirsiniz.  
  
- `keyExp2`  
  
     İsteğe bağlı. Bileşik anahtar oluşturmak için `keyExp1` ile birleştirilen bir veya daha fazla ek anahtar.  
  
- `aggregateList`  
  
     Gerekli. Grupların nasıl toplanacağına ilişkin bir veya daha fazla ifade. Gruplanmış sonuçların üye adını belirlemek için, aşağıdaki biçimlerden birinde olabilecek `Group` anahtar sözcüğünü kullanın:  
  
    ```vb  
    Into Group  
    ```  
  
     veya  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     Gruba uygulanacak toplama işlevlerini de ekleyebilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir sorgunun sonuçlarını gruplara bölmek için `Group By` yan tümcesini kullanabilirsiniz. Gruplandırma bir anahtara veya birden çok anahtardan oluşan bileşik anahtara göre belirlenir. Eşleşen anahtar değerleriyle ilişkili öğeler aynı gruba dahil edilir.  
  
 @No__t-1 yan tümcesinin `aggregateList` parametresini ve gruba başvurmak için kullanılan üye adını belirlemek için `Group` anahtar sözcüğünü kullanırsınız. Gruplanmış öğelerin değerlerini hesaplamak için `Into` yan tümcesine toplama işlevleri de ekleyebilirsiniz. Standart toplama işlevlerinin bir listesi için bkz. [Aggregate yan tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, konumlarına (ülke/bölge) göre müşterilerin bir listesini gruplandırır ve her bir gruptaki müşterilerin sayısını sağlar. Sonuçlar ülke/bölge adına göre sıralanır. Gruplanmış sonuçlar şehir adına göre sıralanır.  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By Yan Tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Aggregate Yan Tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Group Join Yan Tümcesi](../../../visual-basic/language-reference/queries/group-join-clause.md)
