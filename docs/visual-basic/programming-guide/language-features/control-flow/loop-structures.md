---
title: Çevrim Yapıları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: 56165eecce5e73c4e06235dac1691774fb39b794
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906873"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="5b86d-102">Çevrim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b86d-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="5b86d-103">Visual Basic döngü yapıları, bir veya daha fazla kod satırlarını art arda çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5b86d-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="5b86d-104">Bir koşul olana kadar döngü yapısı deyimlerinde yineleyebilirsiniz `True`, bir koşul olana kadar `False`, belirtilen numarası sayısı veya bir kez her öğe için bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="5b86d-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="5b86d-105">Aşağıdaki resimde, bir koşul true olana kadar bir dizi ifadeleri çalıştırılan bir döngü yapısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5b86d-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![Do gösteren akış çizelgesi... Döngü kadar.](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="5b86d-107">While döngülerini</span><span class="sxs-lookup"><span data-stu-id="5b86d-107">While Loops</span></span>  
 <span data-ttu-id="5b86d-108">`While`... `End While` oluşturma deyimleri bir dizi koşul içinde belirtilen sürece çalıştırır `While` deyimi `True`.</span><span class="sxs-lookup"><span data-stu-id="5b86d-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="5b86d-109">Daha fazla bilgi için [sırada... End While deyimi](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5b86d-109">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="5b86d-110">Döngüler yapın</span><span class="sxs-lookup"><span data-stu-id="5b86d-110">Do Loops</span></span>  
 <span data-ttu-id="5b86d-111">`Do`... `Loop` oluşturma, test başına veya sonuna kadar döngü yapısı bir koşulu olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b86d-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="5b86d-112">Koşul kalırken döngüyü verilip verilmeyeceğini belirtebilirsiniz `True` veya oluncaya kadar `True`.</span><span class="sxs-lookup"><span data-stu-id="5b86d-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="5b86d-113">Daha fazla bilgi için [yapın... Döngü deyimi](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5b86d-113">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="5b86d-114">Döngüler için</span><span class="sxs-lookup"><span data-stu-id="5b86d-114">For Loops</span></span>  
 <span data-ttu-id="5b86d-115">`For`... `Next` yapım kümesi birkaç kez döngü gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="5b86d-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="5b86d-116">Bir döngü denetim değişkeni olarak da adlandırılan kullanan bir *sayacı*yinelemeleri izlemek için.</span><span class="sxs-lookup"><span data-stu-id="5b86d-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="5b86d-117">Başlangıç ve bitiş değerlerini Bu sayaç için belirtin ve isteğe bağlı olarak, bir yineleme sonraki artırır tutarı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b86d-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="5b86d-118">Daha fazla bilgi için [için... Sonraki deyimi](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5b86d-118">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="5b86d-119">Her döngü için</span><span class="sxs-lookup"><span data-stu-id="5b86d-119">For Each Loops</span></span>  
 <span data-ttu-id="5b86d-120">`For Each`... `Next` oluşturma bir koleksiyondaki her öğe için bir kez ifadeler kümesi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5b86d-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="5b86d-121">Döngü denetim değişkeni belirtin, ancak başlangıç veya bitiş değerlerinin de belirlemek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b86d-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="5b86d-122">Nesne, salt okunur.[For Each...Next Deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)</span><span class="sxs-lookup"><span data-stu-id="5b86d-122">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b86d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b86d-123">See also</span></span>

- [<span data-ttu-id="5b86d-124">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="5b86d-124">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="5b86d-125">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="5b86d-125">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="5b86d-126">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="5b86d-126">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="5b86d-127">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="5b86d-127">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
