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
ms.openlocfilehash: 34c0fd239d9e08dab4a107cb8447941e7ab3ecbe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480378"
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
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorgular](../../../visual-basic/language-reference/queries/index.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
