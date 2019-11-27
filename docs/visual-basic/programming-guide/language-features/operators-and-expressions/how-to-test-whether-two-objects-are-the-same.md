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
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="4e784-102">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e784-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="4e784-103">Nesnelere başvuran iki değişkeniniz varsa, aynı örneğe başvurıp başvurmadığını öğrenmek için `Is` veya `IsNot` işlecini ya da her ikisini birden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e784-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="4e784-104">İki nesnenin aynı olup olmadığını test etmek için</span><span class="sxs-lookup"><span data-stu-id="4e784-104">To test whether two objects are the same</span></span>  
  
- <span data-ttu-id="4e784-105">Işleç olarak iki değişkenlerle birlikte [, işleç](../../../../visual-basic/language-reference/operators/is-operator.md) veya [IsNot işlecini](../../../../visual-basic/language-reference/operators/isnot-operator.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="4e784-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="4e784-106">İki nesnenin aynı örneğe başvurdığına bağlı olarak belirli bir eylem yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e784-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="4e784-107">Yukarıdaki örnekte denetim `c`, form `f`etkin denetim ile karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="4e784-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="4e784-108">Etkin denetim yoksa veya bir tane varsa ancak `c`aynı denetim örneği değilse, `If` ifade başarısız olur ve yordam daha fazla işleme olmadan döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4e784-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="4e784-109">`Is` veya `IsNot` kullanıp kullanmayacağınızı sizin için kişisel kolaylık sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e784-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="4e784-110">Bunlardan biri, belirli bir ifadede kullanmaktan daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="4e784-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e784-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e784-111">See also</span></span>

- [<span data-ttu-id="4e784-112">Visual Basic karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="4e784-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
