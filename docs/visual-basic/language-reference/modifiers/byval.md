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
ms.openlocfilehash: 076289ff303dce58f036d6c7cb1505b151da19f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602989"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Bağımsız değişken çağrılan yordamı veya özellik çağıran kodu değişkeninde temel bir değişkenin değerini değiştiremezsiniz şekilde geçirilir belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `ByVal` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanımını gösteren `ByVal` parametre bir başvuru türü bağımsız değişkeniyle mekanizması geçirme. Örnekte, bağımsız değişken değer `c1`, sınıfının bir örneği `Class1`. `ByVal` başvuru bağımsız değişkeni, temel alınan değeri değiştirmelerini yordamları kodda `c1`, erişilebilir alanlarını ve özelliklerini korumaz ancak `c1`.  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)  
 [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
