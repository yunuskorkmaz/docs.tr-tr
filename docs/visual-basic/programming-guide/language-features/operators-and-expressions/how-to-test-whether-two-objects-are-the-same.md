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
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="14802-102">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14802-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="14802-103">Nesnelere atıfta iki değişken varsa ya da kullanabilirsiniz `Is` veya `IsNot` işleci veya her ikisini de aynı örneğine bakın olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="14802-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="14802-104">İki nesnenin aynı olup olmadığını sınamak için</span><span class="sxs-lookup"><span data-stu-id="14802-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="14802-105">Kullanım [Is işlecini](../../../../visual-basic/language-reference/operators/is-operator.md) veya [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md) işlenen olarak iki değişkenleriyle.</span><span class="sxs-lookup"><span data-stu-id="14802-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 <span data-ttu-id="14802-106">Olup iki nesnenin aynı örneğine başvuru bağlı olarak belirli bir eylemi almak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14802-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="14802-107">Önceki örnekte denetim karşılaştırır `c` form üzerinde etkin denetim karşı `f`.</span><span class="sxs-lookup"><span data-stu-id="14802-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="14802-108">Etkin bir denetim yok ya da varsa bir ancak değil aynı denetim örneği olarak `c`, sonra `If` deyimi başarısız oluyor ve yordam döndürür başka bir işleme olmadan.</span><span class="sxs-lookup"><span data-stu-id="14802-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="14802-109">Kullansanız `Is` veya `IsNot` size kişisel kolaylık konudur.</span><span class="sxs-lookup"><span data-stu-id="14802-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="14802-110">Bir diğerinden belirli bir ifadede okumak daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="14802-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14802-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14802-111">See Also</span></span>  
 [<span data-ttu-id="14802-112">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="14802-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
