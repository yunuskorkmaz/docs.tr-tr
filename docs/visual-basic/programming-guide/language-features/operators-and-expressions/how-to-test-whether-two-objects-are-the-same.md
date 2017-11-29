---
title: "Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76f5c19386cce84207f80d217326d2e3babf4e44
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
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
