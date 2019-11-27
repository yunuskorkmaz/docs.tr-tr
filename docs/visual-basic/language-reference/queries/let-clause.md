---
title: Let Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 63eaf97016db259870eb77199651ecbdc5f809c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350429"
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
 `Let` yan tümcesi, her sorgu sonucu için değerleri hesaplamanızı ve bir diğer ad kullanarak bunları başvurmanızı sağlar. Diğer ad, `Where` yan tümcesi gibi diğer yan tümcelerde kullanılabilir. `Let` yan tümcesi, sorguda yer alan bir ifade yan tümcesi için bir diğer ad belirtebileceğiniz ve ifade yan tümcesinin her kullanıldığı her seferinde yerine geçecek bir sorgu deyimi oluşturmanıza olanak sağlar.  
  
 `Let` yan tümcesine istediğiniz sayıda `variable` ve `expression` ataması ekleyebilirsiniz. Her atamayı virgülle ayırın (,).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, ürünlerde yüzde 10 indirimi hesaplamak için `Let` yan tümcesini kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
