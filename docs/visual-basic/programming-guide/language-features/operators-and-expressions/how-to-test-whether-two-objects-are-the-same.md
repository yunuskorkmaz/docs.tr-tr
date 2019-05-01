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
ms.openlocfilehash: dbb268175d197e7b931af45a98f3a273c593e5a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864383"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="04c91-102">Nasıl yapılır: İki nesnenin aynı (Visual Basic) olup olmadığını test etme</span><span class="sxs-lookup"><span data-stu-id="04c91-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="04c91-103">Nesnelere atıfta iki değişken varsa, kullanabilirsiniz `Is` veya `IsNot` işleci veya her ikisi de aynı örneğine başvurmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="04c91-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="04c91-104">İki nesnenin aynı olup olmadığını test etmek için</span><span class="sxs-lookup"><span data-stu-id="04c91-104">To test whether two objects are the same</span></span>  
  
- <span data-ttu-id="04c91-105">Kullanım [işleci olan](../../../../visual-basic/language-reference/operators/is-operator.md) veya [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md) işlenen olarak iki değişken ile.</span><span class="sxs-lookup"><span data-stu-id="04c91-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="04c91-106">Olup iki nesnenin aynı örneğe atıfta bağlı olarak belirli bir eylem almak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04c91-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="04c91-107">Yukarıdaki örnekte denetim karşılaştırır `c` form altformdaki etkin denetimi karşı `f`.</span><span class="sxs-lookup"><span data-stu-id="04c91-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="04c91-108">Etkin bir denetim yok ya da varsa bir ancak değil aynı denetim örneğine `c`, ardından `If` deyim başarısız olur ve yordamı daha fazla işleme olmadan döndürür.</span><span class="sxs-lookup"><span data-stu-id="04c91-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="04c91-109">Kullanıp `Is` veya `IsNot` kişisel kolaylık sağlamak için bir konudur.</span><span class="sxs-lookup"><span data-stu-id="04c91-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="04c91-110">Bir diğerinden belirli bir ifadede daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="04c91-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04c91-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04c91-111">See also</span></span>

- [<span data-ttu-id="04c91-112">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="04c91-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
