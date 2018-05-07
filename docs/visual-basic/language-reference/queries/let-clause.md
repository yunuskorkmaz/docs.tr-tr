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
ms.openlocfilehash: 6484da5329c8240735b7c35f506637dd01cbeda4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="let-clause-visual-basic"></a>Let Tümcesi (Visual Basic)
Bir değeri hesaplar ve sorgu içinde yeni bir değişkene atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`variable`|Gerekli. Sağlanan ifade sonuçlarını başvurmak için kullanılan bir diğer ad.|  
|`expression`|Gerekli. Değerlendirilecek ve belirtilen değişkenine atanan bir ifade.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Let` Yan tümcesi, her biri için değerleri sorgu sonucu ve bir diğer ad kullanarak başvuru işlem olanak tanır. Diğer ad diğer yan tümcelerinde gibi kullanılabilir `Where` yan tümcesi. `Let` Yan tümcesi, çünkü sorguda bir ifade yan tümcesi için diğer ad belirtin ve ifade yan tümcesinde kullanılan her zaman diğer adı yerine okunması daha kolay olan bir sorgu deyimi oluşturmanıza olanak sağlar.  
  
 Herhangi bir sayıda içerebilir `variable` ve `expression` atamalarını `Let` yan tümcesi. Her bir atama virgülle (,) ayırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Let` yüzde 10 indirim ürünlerine hesaplamak için yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorgular](../../../visual-basic/language-reference/queries/queries.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
