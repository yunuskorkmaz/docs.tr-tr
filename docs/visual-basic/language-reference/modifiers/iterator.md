---
title: Yineleyici (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 499949d1f4c20e1f465355bd076ba39f1496779b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920724"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="20bf4-102">Yineleyici (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20bf4-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="20bf4-103">Belirleyen bir işlev veya `Get` erişimcisinin yineleyici olduğunu.</span><span class="sxs-lookup"><span data-stu-id="20bf4-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20bf4-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20bf4-104">Remarks</span></span>  
 <span data-ttu-id="20bf4-105">Bir *yineleyici* bir koleksiyon üzerinde özel yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="20bf4-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="20bf4-106">Yineleyici [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) her öğe aynı anda koleksiyonundaki bir dönüş deyimi.</span><span class="sxs-lookup"><span data-stu-id="20bf4-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="20bf4-107">Olduğunda bir `Yield` deyimine ulaşıldığında, kodun geçerli konumu korunur.</span><span class="sxs-lookup"><span data-stu-id="20bf4-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="20bf4-108">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="20bf4-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="20bf4-109">Bir yineleyiciyi bir işlev veya olarak uygulanabilir bir `Get` erişimci özelliği tanımı.</span><span class="sxs-lookup"><span data-stu-id="20bf4-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="20bf4-110">`Iterator` Değiştirici görünür yineleyici işlevi bildiriminde veya `Get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="20bf4-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="20bf4-111">Bir yineleyici kullanarak istemci koddan çağırmak bir [her biri için... Sonraki deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="20bf4-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="20bf4-112">Bir yineleyici işlevinin dönüş türü veya `Get` erişimcisi olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="20bf4-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="20bf4-113">Bir yineleyicinin içeremez `ByRef` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="20bf4-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="20bf4-114">Bir yineleyiciyi bir olay, örnek oluşturucusu, statik oluşturucu veya statik yok Edicisi olamaz.</span><span class="sxs-lookup"><span data-stu-id="20bf4-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="20bf4-115">Bir yineleyici anonim bir işlevdir olabilir.</span><span class="sxs-lookup"><span data-stu-id="20bf4-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="20bf4-116">Daha fazla bilgi için [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="20bf4-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="20bf4-117">Kullanım</span><span class="sxs-lookup"><span data-stu-id="20bf4-117">Usage</span></span>  
 <span data-ttu-id="20bf4-118">`Iterator` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="20bf4-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="20bf4-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="20bf4-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="20bf4-120">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="20bf4-120">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="20bf4-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="20bf4-121">Example</span></span>  
 <span data-ttu-id="20bf4-122">Aşağıdaki örnek, bir yineleyici işlevi gösterir.</span><span class="sxs-lookup"><span data-stu-id="20bf4-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="20bf4-123">Yineleyici işleve sahip bir `Yield` içindeki bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="20bf4-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="20bf4-124">Her bir yinelemesini [her](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyiminin gövdesinde `Main` bir çağrı oluşturur `Power` yineleyici işlevi.</span><span class="sxs-lookup"><span data-stu-id="20bf4-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="20bf4-125">Her yineleyici işleve çağrı için sonraki yürütme devam eder `Yield` sıradaki yinelemesi süresince gerçekleşen deyimi `For…Next` döngü.</span><span class="sxs-lookup"><span data-stu-id="20bf4-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="20bf4-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="20bf4-126">Example</span></span>  
 <span data-ttu-id="20bf4-127">Aşağıdaki örnek, gösterir bir `Get` bir yineleyici erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="20bf4-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="20bf4-128">`Iterator` Özellik bildiriminde bir değiştiricidir.</span><span class="sxs-lookup"><span data-stu-id="20bf4-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="20bf4-129">Diğer örnekler için [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="20bf4-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20bf4-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20bf4-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="20bf4-131">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="20bf4-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="20bf4-132">Yield Deyimi</span><span class="sxs-lookup"><span data-stu-id="20bf4-132">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
