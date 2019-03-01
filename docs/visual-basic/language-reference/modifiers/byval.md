---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: edee47e41ca78175a6fb24ed5eac255c03de0901
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972584"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Bağımsız değişken çağrılan yordam veya özellik çağıran koddaki bağımsız değişken arka plandaki bir değişkenin değerini değiştiremezsiniz şekilde geçirildiğini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `ByVal` Bu bağlamda değiştirici kullanılabilir:  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kullanımını gösterir `ByVal` parametre mekanizması ile bir başvuru türü bağımsız değişkeni geçirme. Örnekte, bağımsız değişken olan `c1`, sınıfının bir örneğini `Class1`. `ByVal` yordamları kodda başvuru bağımsız değişkeni, temel alınan değerini değiştirmesini engeller `c1`, ancak erişilebilir alanlarına ve özelliklerine korumaz `c1`.  
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
