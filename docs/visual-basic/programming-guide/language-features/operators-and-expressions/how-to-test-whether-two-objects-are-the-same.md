---
title: 'Nasıl yapılır: İki nesnenin aynı (Visual Basic) olup olmadığını test etme'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 4130dfbe70682e28b6bb15db633ede2790e20aa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595558"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="34c80-102">Nasıl yapılır: İki nesnenin aynı (Visual Basic) olup olmadığını test etme</span><span class="sxs-lookup"><span data-stu-id="34c80-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="34c80-103">Nesnelere atıfta iki değişken varsa, kullanabilirsiniz `Is` veya `IsNot` işleci veya her ikisi de aynı örneğine başvurmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="34c80-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="34c80-104">İki nesnenin aynı olup olmadığını test etmek için</span><span class="sxs-lookup"><span data-stu-id="34c80-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="34c80-105">Kullanım [işleci olan](../../../../visual-basic/language-reference/operators/is-operator.md) veya [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md) işlenen olarak iki değişken ile.</span><span class="sxs-lookup"><span data-stu-id="34c80-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 <span data-ttu-id="34c80-106">Olup iki nesnenin aynı örneğe atıfta bağlı olarak belirli bir eylem almak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34c80-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="34c80-107">Yukarıdaki örnekte denetim karşılaştırır `c` form altformdaki etkin denetimi karşı `f`.</span><span class="sxs-lookup"><span data-stu-id="34c80-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="34c80-108">Etkin bir denetim yok ya da varsa bir ancak değil aynı denetim örneğine `c`, ardından `If` deyim başarısız olur ve yordamı daha fazla işleme olmadan döndürür.</span><span class="sxs-lookup"><span data-stu-id="34c80-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="34c80-109">Kullanıp `Is` veya `IsNot` kişisel kolaylık sağlamak için bir konudur.</span><span class="sxs-lookup"><span data-stu-id="34c80-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="34c80-110">Bir diğerinden belirli bir ifadede daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="34c80-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34c80-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34c80-111">See also</span></span>
- [<span data-ttu-id="34c80-112">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="34c80-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
