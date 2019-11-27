---
title: 'Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 22e8e1e688d9e3bc3804899103ee78814aac235b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343626"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme (Visual Basic)
Nesnelere başvuran iki değişkeniniz varsa, aynı örneğe başvurıp başvurmadığını öğrenmek için `Is` veya `IsNot` işlecini ya da her ikisini birden kullanabilirsiniz.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>İki nesnenin aynı olup olmadığını test etmek için  
  
- Işleç olarak iki değişkenlerle birlikte [, işleç](../../../../visual-basic/language-reference/operators/is-operator.md) veya [IsNot işlecini](../../../../visual-basic/language-reference/operators/isnot-operator.md) kullanın.  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 İki nesnenin aynı örneğe başvurdığına bağlı olarak belirli bir eylem yapmak isteyebilirsiniz. Yukarıdaki örnekte denetim `c`, form `f`etkin denetim ile karşılaştırılır. Etkin denetim yoksa veya bir tane varsa ancak `c`aynı denetim örneği değilse, `If` ifade başarısız olur ve yordam daha fazla işleme olmadan döndürülür.  
  
 `Is` veya `IsNot` kullanıp kullanmayacağınızı sizin için kişisel kolaylık sağlar. Bunlardan biri, belirli bir ifadede kullanmaktan daha kolay olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic karşılaştırma Işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
