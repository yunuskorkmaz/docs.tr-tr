---
title: Let Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: ff298f001a2d865446436e8099a2fbbef593a00a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828721"
---
# <a name="let-clause-visual-basic"></a>Let Tümcesi (Visual Basic)
Bir değeri hesaplar ve bir sorgu içinde yeni bir değişkene atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`variable`|Gerekli. Sağlanan ifade sonuçlarını başvurmak için kullanılan bir diğer ad.|  
|`expression`|Gerekli. Değerlendirilecek ve belirtilen değişkene atanan bir ifade.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Let` Yan tümcesi işlem değerleri her sorgu sonuç ve bir diğer ad kullanarak başvuru olanak sağlar. Diğer ad diğer yan tümcelerinde gibi kullanılabilir `Where` yan tümcesi. `Let` Yan tümcesi çünkü Sorguda ifade yan tümcesi için bir diğer ad belirtin ve ifade yan tümcesi kullanıldığında her zaman diğer adı yerine daha kolay olan bir sorgu deyimi oluşturmanıza olanak sağlar.  
  
 Herhangi bir sayıda içerebilir `variable` ve `expression` atamalarını `Let` yan tümcesi. Her atama virgülle (,) ayırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Let` ürünleri yüzde 10 indirim işlem yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
