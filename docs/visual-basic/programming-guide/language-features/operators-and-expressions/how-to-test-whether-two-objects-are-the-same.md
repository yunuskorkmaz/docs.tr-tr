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
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="98817-102">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98817-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="98817-103">Nesnelere atıfta iki değişken varsa ya da kullanabilirsiniz `Is` veya `IsNot` işleci veya her ikisini de aynı örneğine bakın olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="98817-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="98817-104">İki nesnenin aynı olup olmadığını sınamak için</span><span class="sxs-lookup"><span data-stu-id="98817-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="98817-105">Kullanım [Is işlecini](../../../../visual-basic/language-reference/operators/is-operator.md) veya [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md) işlenen olarak iki değişkenleriyle.</span><span class="sxs-lookup"><span data-stu-id="98817-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 <span data-ttu-id="98817-106">Olup iki nesnenin aynı örneğine başvuru bağlı olarak belirli bir eylemi almak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98817-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="98817-107">Önceki örnekte denetim karşılaştırır `c` form üzerinde etkin denetim karşı `f`.</span><span class="sxs-lookup"><span data-stu-id="98817-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="98817-108">Etkin bir denetim yok ya da varsa bir ancak değil aynı denetim örneği olarak `c`, sonra `If` deyimi başarısız oluyor ve yordam döndürür başka bir işleme olmadan.</span><span class="sxs-lookup"><span data-stu-id="98817-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="98817-109">Kullansanız `Is` veya `IsNot` size kişisel kolaylık konudur.</span><span class="sxs-lookup"><span data-stu-id="98817-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="98817-110">Bir diğerinden belirli bir ifadede okumak daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="98817-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98817-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="98817-111">See Also</span></span>  
 [<span data-ttu-id="98817-112">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="98817-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
