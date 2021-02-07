---
description: 'Daha fazla bilgi edinin: yineleyici (Visual Basic)'
title: Iterator
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 7a3329ba23a3f2487343b332f3bb9c4b19c36496
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730531"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="3fa86-103">Yineleyici (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fa86-103">Iterator (Visual Basic)</span></span>

<span data-ttu-id="3fa86-104">Bir işlevin veya `Get` erişimcinin bir yineleyici olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fa86-104">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fa86-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fa86-105">Remarks</span></span>  

 <span data-ttu-id="3fa86-106">*Yineleyici* bir koleksiyon üzerinde özel bir yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3fa86-106">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="3fa86-107">Bir yineleyici, koleksiyondaki her öğeyi tek seferde döndürmek için [yield](../statements/yield-statement.md) ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3fa86-107">An iterator uses the [Yield](../statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="3fa86-108">Bir `Yield` ifadeye ulaşıldığında, koddaki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="3fa86-108">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="3fa86-109">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="3fa86-109">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="3fa86-110">Yineleyici, bir işlev olarak veya bir `Get` özellik tanımının erişimcisi olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3fa86-110">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="3fa86-111">`Iterator`Değiştirici, Yineleyici işlevinin veya `Get` erişimcinin bildiriminde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3fa86-111">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="3fa86-112">Her biri Için bir kullanarak istemci kodundan bir yineleyici çağırın [... Sonraki Ifade](../statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3fa86-112">You call an iterator from client code by using a [For Each...Next Statement](../statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="3fa86-113">Yineleyici işlevinin veya `Get` erişimcisinin dönüş türü <xref:System.Collections.IEnumerable> ,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> , veya olabilir <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="3fa86-113">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="3fa86-114">Yineleyicinin herhangi bir `ByRef` parametresi olamaz.</span><span class="sxs-lookup"><span data-stu-id="3fa86-114">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="3fa86-115">Bir olay, örnek Oluşturucu, statik oluşturucu veya statik yok edicisi içinde yineleyici olamaz.</span><span class="sxs-lookup"><span data-stu-id="3fa86-115">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="3fa86-116">Yineleyici bir anonim işlev olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fa86-116">An iterator can be an anonymous function.</span></span> <span data-ttu-id="3fa86-117">Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="3fa86-117">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="3fa86-118">Kullanım</span><span class="sxs-lookup"><span data-stu-id="3fa86-118">Usage</span></span>  

 <span data-ttu-id="3fa86-119">`Iterator`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="3fa86-119">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="3fa86-120">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="3fa86-120">Function Statement</span></span>](../statements/function-statement.md)  
  
- [<span data-ttu-id="3fa86-121">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="3fa86-121">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="3fa86-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fa86-122">Example</span></span>  

 <span data-ttu-id="3fa86-123">Aşağıdaki örnekte bir yineleyici işlevi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3fa86-123">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="3fa86-124">Yineleyici işlevinin, `Yield` için içindeki bir ifade vardır [... Sonraki](../statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="3fa86-124">The iterator function has a `Yield` statement that is inside a [For…Next](../statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="3fa86-125">İçindeki [her bir for](../statements/for-each-next-statement.md) Ifadesinin gövdesi için her yineleme, `Main` Yineleyici işlevine bir çağrı oluşturur `Power` .</span><span class="sxs-lookup"><span data-stu-id="3fa86-125">Each iteration of the [For Each](../statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="3fa86-126">Yineleyici işlevine yapılan her çağrı, `Yield` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan deyimin bir sonraki yürütmeye ilerler `For…Next` .</span><span class="sxs-lookup"><span data-stu-id="3fa86-126">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="3fa86-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fa86-127">Example</span></span>  

 <span data-ttu-id="3fa86-128">Aşağıdaki örnek, `Get` Yineleyici olan bir erişimciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fa86-128">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="3fa86-129">`Iterator`Değiştirici, özellik bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="3fa86-129">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="3fa86-130">Ek örnekler için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="3fa86-130">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fa86-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fa86-131">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="3fa86-132">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="3fa86-132">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="3fa86-133">Yield Deyimi</span><span class="sxs-lookup"><span data-stu-id="3fa86-133">Yield Statement</span></span>](../statements/yield-statement.md)
