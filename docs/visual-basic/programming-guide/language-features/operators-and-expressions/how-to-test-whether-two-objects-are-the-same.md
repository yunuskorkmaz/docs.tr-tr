---
title: 'Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 005c91e6f4ec556a7e1bf255b47c8276a5d3d185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647611"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme (Visual Basic)
Nesnelere atıfta iki değişken varsa ya da kullanabilirsiniz `Is` veya `IsNot` işleci veya her ikisini de aynı örneğine bakın olup olmadığını belirlemek için.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>İki nesnenin aynı olup olmadığını sınamak için  
  
-   Kullanım [Is işlecini](../../../../visual-basic/language-reference/operators/is-operator.md) veya [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md) işlenen olarak iki değişkenleriyle.  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 Olup iki nesnenin aynı örneğine başvuru bağlı olarak belirli bir eylemi almak isteyebilirsiniz. Önceki örnekte denetim karşılaştırır `c` form üzerinde etkin denetim karşı `f`. Etkin bir denetim yok ya da varsa bir ancak değil aynı denetim örneği olarak `c`, sonra `If` deyimi başarısız oluyor ve yordam döndürür başka bir işleme olmadan.  
  
 Kullansanız `Is` veya `IsNot` size kişisel kolaylık konudur. Bir diğerinden belirli bir ifadede okumak daha kolay olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
