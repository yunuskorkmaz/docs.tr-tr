---
title: Çevrim Yapıları
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
ms.openlocfilehash: 0a75205a7d52c332094d624d082e5db3e89447f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353922"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="c1a13-102">Çevrim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1a13-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="c1a13-103">Visual Basic döngüsü yapıları, bir veya daha fazla kod kaldı satırını çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1a13-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="c1a13-104">Bir koşul `True`, bir koşul `False`, belirtilen sayıda kez veya bir koleksiyondaki her öğe için bir kez olmak üzere, deyimi bir döngü yapısında yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1a13-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="c1a13-105">Aşağıdaki çizimde, bir koşul doğru olana kadar deyim kümesini çalıştıran bir döngü yapısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c1a13-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![Bir do gösteren akış grafiği... Until döngüsü.](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="c1a13-107">While döngüleri</span><span class="sxs-lookup"><span data-stu-id="c1a13-107">While Loops</span></span>  
 <span data-ttu-id="c1a13-108">`While`...`End While` oluşturma, `While` deyiminde belirtilen koşul `True`olduğu sürece bir deyim kümesi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="c1a13-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="c1a13-109">Daha fazla bilgi için bkz [. while... End while bildirisi](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c1a13-109">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="c1a13-110">Do döngüleri</span><span class="sxs-lookup"><span data-stu-id="c1a13-110">Do Loops</span></span>  
 <span data-ttu-id="c1a13-111">`Do`...`Loop` oluşturma, bir koşulu bir döngü yapısının başlangıcında veya sonunda test etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1a13-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="c1a13-112">Ayrıca, koşul `True` kaldığında veya `True`hale gelene kadar döngünün tekraranıp tekrarlanmayacağını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1a13-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="c1a13-113">Daha fazla bilgi için bkz [. do... Loop deyimleri](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c1a13-113">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="c1a13-114">Döngüler için</span><span class="sxs-lookup"><span data-stu-id="c1a13-114">For Loops</span></span>  
 <span data-ttu-id="c1a13-115">`For`...`Next` oluşturma döngüyü bir dizi kez uygular.</span><span class="sxs-lookup"><span data-stu-id="c1a13-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="c1a13-116">Tekrarları izlemek için *sayaç*olarak da adlandırılan bir döngü denetim değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1a13-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="c1a13-117">Bu sayacın başlangıç ve bitiş değerlerini belirtirsiniz ve isteğe bağlı olarak bir tekrardan bir yinelemeden artarak miktarı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1a13-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="c1a13-118">Daha fazla bilgi için bkz.... [ Sonraki Ifade](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c1a13-118">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="c1a13-119">Her döngü için</span><span class="sxs-lookup"><span data-stu-id="c1a13-119">For Each Loops</span></span>  
 <span data-ttu-id="c1a13-120">`For Each`...`Next` oluşturma bir koleksiyondaki her öğe için bir deyim kümesi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="c1a13-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="c1a13-121">Döngü denetim değişkenini belirtirsiniz, ancak bunun başlangıç veya bitiş değerlerini belirlemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c1a13-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="c1a13-122">Daha fazla bilgi için bkz [. her biri için... Sonraki Ifade](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c1a13-122">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a13-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1a13-123">See also</span></span>

- [<span data-ttu-id="c1a13-124">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="c1a13-124">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="c1a13-125">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="c1a13-125">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="c1a13-126">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="c1a13-126">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="c1a13-127">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="c1a13-127">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
