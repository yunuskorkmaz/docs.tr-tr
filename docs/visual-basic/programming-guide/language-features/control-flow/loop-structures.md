---
title: Döngü Yapıları
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
ms.openlocfilehash: 3f60e9dc83dc7174e765903be13f2870ea40ce4c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403530"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="4d892-102">Çevrim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d892-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="4d892-103">Visual Basic döngüsü yapıları, bir veya daha fazla kod kaldı satırını çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d892-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="4d892-104">Bir koşul, bir `True` koşul, `False` belirtilen sayıda kez veya bir koleksiyondaki her öğe için bir kez olmak üzere bir döngü yapısındaki deyimleri tekrarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d892-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="4d892-105">Aşağıdaki çizimde, bir koşul doğru olana kadar deyim kümesini çalıştıran bir döngü yapısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="4d892-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![Bir do gösteren akış grafiği... Until döngüsü.](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="4d892-107">While döngüleri</span><span class="sxs-lookup"><span data-stu-id="4d892-107">While Loops</span></span>  
 <span data-ttu-id="4d892-108">`While`... `End While` İnşaat, deyimde belirtilen koşul olduğu sürece bir deyim kümesi çalıştırır `While` `True` .</span><span class="sxs-lookup"><span data-stu-id="4d892-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="4d892-109">Daha fazla bilgi için bkz [. while... End while bildirisi](../../../language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4d892-109">For more information, see [While...End While Statement](../../../language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="4d892-110">Do döngüleri</span><span class="sxs-lookup"><span data-stu-id="4d892-110">Do Loops</span></span>  
 <span data-ttu-id="4d892-111">`Do`... `Loop` Oluşturma bir koşulu bir döngü yapısının başlangıcında veya sonunda test etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d892-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="4d892-112">Ayrıca, koşul kaldığında veya olana kadar döngünün tekraranıp tekrarlanmayacağını belirtebilirsiniz `True` `True` .</span><span class="sxs-lookup"><span data-stu-id="4d892-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="4d892-113">Daha fazla bilgi için bkz [. do... Loop deyimleri](../../../language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4d892-113">For more information, see [Do...Loop Statement](../../../language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="4d892-114">Döngüler için</span><span class="sxs-lookup"><span data-stu-id="4d892-114">For Loops</span></span>  
 <span data-ttu-id="4d892-115">`For`... `Next` Oluşturma, döngüye bir dizi kez uygular.</span><span class="sxs-lookup"><span data-stu-id="4d892-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="4d892-116">Tekrarları izlemek için *sayaç*olarak da adlandırılan bir döngü denetim değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="4d892-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="4d892-117">Bu sayacın başlangıç ve bitiş değerlerini belirtirsiniz ve isteğe bağlı olarak bir tekrardan bir yinelemeden artarak miktarı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d892-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="4d892-118">Daha fazla bilgi için bkz.... [ Sonraki Ifade](../../../language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4d892-118">For more information, see [For...Next Statement](../../../language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="4d892-119">Her döngü için</span><span class="sxs-lookup"><span data-stu-id="4d892-119">For Each Loops</span></span>  
 <span data-ttu-id="4d892-120">`For Each`... `Next` İnşaatı bir koleksiyondaki her öğe için bir deyim kümesi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="4d892-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="4d892-121">Döngü denetim değişkenini belirtirsiniz, ancak bunun başlangıç veya bitiş değerlerini belirlemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4d892-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="4d892-122">Daha fazla bilgi için bkz [. her biri için... Sonraki Ifade](../../../language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4d892-122">For more information, see [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d892-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d892-123">See also</span></span>

- [<span data-ttu-id="4d892-124">Denetim akışı</span><span class="sxs-lookup"><span data-stu-id="4d892-124">Control Flow</span></span>](index.md)
- [<span data-ttu-id="4d892-125">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="4d892-125">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="4d892-126">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="4d892-126">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="4d892-127">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="4d892-127">Nested Control Structures</span></span>](nested-control-structures.md)
