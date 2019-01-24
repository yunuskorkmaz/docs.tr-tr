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
ms.openlocfilehash: 6fa87db4fbab961dd1aa526e2ac8ff15b031005b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650086"
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
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
