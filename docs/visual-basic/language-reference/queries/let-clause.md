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
ms.openlocfilehash: 545eefc67d52428470c19b62085fd87927505c7e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972709"
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
