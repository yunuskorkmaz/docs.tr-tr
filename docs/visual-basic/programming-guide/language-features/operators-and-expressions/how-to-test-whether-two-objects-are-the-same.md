---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: Iki nesnenin aynı olup olmadığını test etme (Visual Basic)'
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
ms.openlocfilehash: a0136d9db487ad0ce70b9d55ff8ee014ec30b05a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100435544"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme (Visual Basic)

Nesnelere başvuran iki değişkeniniz varsa, `Is` `IsNot` aynı örneğe başvurıp başvurmadığını öğrenmek için ya da işlecini ya da her ikisini birden kullanabilirsiniz.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>İki nesnenin aynı olup olmadığını test etmek için  
  
- Işleç olarak iki değişkenlerle birlikte [, işleç](../../../language-reference/operators/is-operator.md) veya [IsNot işlecini](../../../language-reference/operators/isnot-operator.md) kullanın.  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 İki nesnenin aynı örneğe başvurdığına bağlı olarak belirli bir eylem yapmak isteyebilirsiniz. Önceki örnekte denetim `c` , formdaki etkin denetimle karşılaştırılır `f` . Etkin denetim yoksa veya bir tane varsa ancak aynı denetim örneği değilse `c` , `If` ifade başarısız olur ve yordam daha fazla işleme olmadan döndürülür.  
  
 `Is`Ya da `IsNot` sizin için kişisel kolaylık olsun. Bunlardan biri, belirli bir ifadede kullanmaktan daha kolay olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de Karşılaştırma İşleçleri](comparison-operators.md)
