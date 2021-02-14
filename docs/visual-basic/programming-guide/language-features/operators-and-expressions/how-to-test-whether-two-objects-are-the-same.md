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
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="66050-103">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66050-103">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>

<span data-ttu-id="66050-104">Nesnelere başvuran iki değişkeniniz varsa, `Is` `IsNot` aynı örneğe başvurıp başvurmadığını öğrenmek için ya da işlecini ya da her ikisini birden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66050-104">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="66050-105">İki nesnenin aynı olup olmadığını test etmek için</span><span class="sxs-lookup"><span data-stu-id="66050-105">To test whether two objects are the same</span></span>  
  
- <span data-ttu-id="66050-106">Işleç olarak iki değişkenlerle birlikte [, işleç](../../../language-reference/operators/is-operator.md) veya [IsNot işlecini](../../../language-reference/operators/isnot-operator.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="66050-106">Use the [Is Operator](../../../language-reference/operators/is-operator.md) or the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="66050-107">İki nesnenin aynı örneğe başvurdığına bağlı olarak belirli bir eylem yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66050-107">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="66050-108">Önceki örnekte denetim `c` , formdaki etkin denetimle karşılaştırılır `f` .</span><span class="sxs-lookup"><span data-stu-id="66050-108">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="66050-109">Etkin denetim yoksa veya bir tane varsa ancak aynı denetim örneği değilse `c` , `If` ifade başarısız olur ve yordam daha fazla işleme olmadan döndürülür.</span><span class="sxs-lookup"><span data-stu-id="66050-109">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="66050-110">`Is`Ya da `IsNot` sizin için kişisel kolaylık olsun.</span><span class="sxs-lookup"><span data-stu-id="66050-110">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="66050-111">Bunlardan biri, belirli bir ifadede kullanmaktan daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="66050-111">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66050-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66050-112">See also</span></span>

- [<span data-ttu-id="66050-113">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="66050-113">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
