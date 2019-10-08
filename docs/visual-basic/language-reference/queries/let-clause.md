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
ms.openlocfilehash: 88166a040823cfefe623f672e556c364d652a7fc
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004734"
---
# <a name="let-clause-visual-basic"></a>Let Tümcesi (Visual Basic)
Bir değeri hesaplar ve sorgu içindeki yeni bir değişkene atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`variable`|Gerekli. Sağlanan ifadenin sonuçlarına başvurmak için kullanılabilecek bir diğer ad.|  
|`expression`|Gerekli. Değerlendirilecek ve belirtilen değişkene atanacak bir ifade.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 yan tümcesi, her sorgu sonucu için değerleri hesaplamanızı ve bir diğer ad kullanarak bunları başvurmanızı sağlar. Diğer ad, `Where` yan tümcesi gibi diğer yan tümcelerde kullanılabilir. @No__t-0 yan tümcesi, sorguda yer alan bir ifade yan tümcesi için bir diğer ad belirtebileceğiniz ve ifade yan tümcesinin her kullanıldığı her seferinde yerine geçecek bir sorgu deyimi oluşturmanıza olanak sağlar.  
  
 @No__t-2 yan tümcesinde herhangi bir sayıda `variable` ve `expression` ataması ekleyebilirsiniz. Her atamayı virgülle ayırın (,).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, ürünlerde yüzde 10 indirimi hesaplamak için `Let` yan tümcesini kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
