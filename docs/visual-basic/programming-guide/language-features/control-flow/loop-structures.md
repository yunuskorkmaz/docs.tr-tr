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
ms.openlocfilehash: 8138609f06d82b53ef5b5afb480e8609461ffc33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647897"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="3dc7e-102">Çevrim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3dc7e-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="3dc7e-103">Visual Basic döngü yapıları, bir veya daha fazla satır kod art arda çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3dc7e-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="3dc7e-104">Bir koşul kadar döngü yapısı deyimlerinde yineleyebilirsiniz `True`, bir koşul kadar `False`, bir sayı çok kez veya bir kez her öğe için bir koleksiyondaki belirtilen.</span><span class="sxs-lookup"><span data-stu-id="3dc7e-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="3dc7e-105">Aşağıdaki çizimde deyimleri bir dizi koşul true olana kadar çalıştırılan döngü yapısı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3dc7e-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true.</span></span>  
  
 <span data-ttu-id="3dc7e-106">![Bir akış çizelgesi... Döngü kadar](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span><span class="sxs-lookup"><span data-stu-id="3dc7e-106">![Flow chart of a Do...Until loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span></span>  
<span data-ttu-id="3dc7e-107">Bir koşul true olana kadar deyimleri kümesi çalıştıran</span><span class="sxs-lookup"><span data-stu-id="3dc7e-107">Running a set of statements until a condition becomes true</span></span>  
  
## <a name="while-loops"></a><span data-ttu-id="3dc7e-108">While döngüler</span><span class="sxs-lookup"><span data-stu-id="3dc7e-108">While Loops</span></span>  
 <span data-ttu-id="3dc7e-109">`While`... `End While` yapım çalıştıran deyimleri bir dizi koşul içinde belirtilen sürece `While` ifadesi `True`.</span><span class="sxs-lookup"><span data-stu-id="3dc7e-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="3dc7e-110">Daha fazla bilgi için bkz: [sırada... End While deyimi](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3dc7e-110">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="3dc7e-111">Döngüler yapın</span><span class="sxs-lookup"><span data-stu-id="3dc7e-111">Do Loops</span></span>  
 <span data-ttu-id="3dc7e-112">`Do`... `Loop` yapım başında veya döngü yapısı sonuna bir koşulu test olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3dc7e-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="3dc7e-113">Ayrıca koşulunu kalırken döngüyü bırakmamayı belirtebilir `True` veya oluncaya kadar `True`.</span><span class="sxs-lookup"><span data-stu-id="3dc7e-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="3dc7e-114">Daha fazla bilgi için bkz: [yapın... Loop deyimi](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3dc7e-114">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="3dc7e-115">Döngüler için</span><span class="sxs-lookup"><span data-stu-id="3dc7e-115">For Loops</span></span>  
 <span data-ttu-id="3dc7e-116">`For`... `Next` yapım kümesi kaç kez döngü gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3dc7e-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="3dc7e-117">Bir for döngüsü denetim değişkeni olarak da bilinir kullanan bir *sayaç*, yinelemeleri izlemek için.</span><span class="sxs-lookup"><span data-stu-id="3dc7e-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="3dc7e-118">Başlangıç ve bitiş değerlerinin bu sayacın belirtin ve isteğe bağlı olarak bir yineleme sonraki artırır tutar belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3dc7e-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="3dc7e-119">Daha fazla bilgi için bkz: [için... Sonraki deyim](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3dc7e-119">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="3dc7e-120">Her döngü için</span><span class="sxs-lookup"><span data-stu-id="3dc7e-120">For Each Loops</span></span>  
 <span data-ttu-id="3dc7e-121">`For Each`... `Next` yapım bir koleksiyondaki her öğe için bir kez deyimleri kümesi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="3dc7e-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="3dc7e-122">For döngüsü denetim değişkeni belirtin, ancak başlangıç veya bitiş değerlerinin için belirlemek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3dc7e-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="3dc7e-123">Daha fazla bilgi için bkz: [For Each... Sonraki deyim](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3dc7e-123">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc7e-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3dc7e-124">See Also</span></span>  
 [<span data-ttu-id="3dc7e-125">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="3dc7e-125">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="3dc7e-126">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="3dc7e-126">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="3dc7e-127">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="3dc7e-127">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="3dc7e-128">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="3dc7e-128">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
