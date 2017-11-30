---
title: Yineleyici (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Iterator
helpviewer_keywords: Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 503d586c0515b4cb53f8ec5656e5fe765cc094a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="86bc8-102">Yineleyici (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86bc8-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="86bc8-103">Belirleyen bir işlevi veya `Get` erişimci yineleyici olduğu.</span><span class="sxs-lookup"><span data-stu-id="86bc8-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86bc8-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86bc8-104">Remarks</span></span>  
 <span data-ttu-id="86bc8-105">Bir *yineleyici* özel bir yineleme içinde bir koleksiyon gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="86bc8-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="86bc8-106">Yineleyici kullanan [verim](../../../visual-basic/language-reference/statements/yield-statement.md) deyimi koleksiyondaki bir birer birer her öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="86bc8-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="86bc8-107">Zaman bir `Yield` deyimi ulaşıldığında, kod geçerli konumda korunur.</span><span class="sxs-lookup"><span data-stu-id="86bc8-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="86bc8-108">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="86bc8-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="86bc8-109">Yineleyici bir işlevi veya olarak uygulanabileceği bir `Get` özelliği tanımı erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="86bc8-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="86bc8-110">`Iterator` Değiştiricisi görünür yineleyici işlevi bildiriminde veya `Get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="86bc8-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="86bc8-111">Yineleyici kullanarak istemci kodundan çağıran bir [For Each... Sonraki deyim](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="86bc8-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="86bc8-112">Bir yineleyici işlevinin dönüş türü veya `Get` erişimci olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="86bc8-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="86bc8-113">Yineleyici içeremez `ByRef` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="86bc8-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="86bc8-114">Yineleyici bir olay, örnek oluşturucusu, statik Oluşturucusu veya statik yıkıcı gerçekleşemez.</span><span class="sxs-lookup"><span data-stu-id="86bc8-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="86bc8-115">Yineleyici adsız bir işlev olabilir.</span><span class="sxs-lookup"><span data-stu-id="86bc8-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="86bc8-116">Daha fazla bilgi için bkz: [yineleyiciler](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="86bc8-116">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="86bc8-117">Yineleyiciler hakkında daha fazla bilgi için bkz: [yineleyiciler](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="86bc8-117">For more information about iterators, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="86bc8-118">Kullanım</span><span class="sxs-lookup"><span data-stu-id="86bc8-118">Usage</span></span>  
 <span data-ttu-id="86bc8-119">`Iterator` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="86bc8-119">The `Iterator` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="86bc8-120">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="86bc8-120">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="86bc8-121">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="86bc8-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="86bc8-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="86bc8-122">Example</span></span>  
 <span data-ttu-id="86bc8-123">Aşağıdaki örnek, bir yineleyici işlevi gösterir.</span><span class="sxs-lookup"><span data-stu-id="86bc8-123">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="86bc8-124">Yineleyici işlevinin bir `Yield` içinde deyimi bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="86bc8-124">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="86bc8-125">Her yinelemesinden [her](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyiminin gövdesinde `Main` yapılan bir çağrı oluşturur `Power` yineleyici işlevi.</span><span class="sxs-lookup"><span data-stu-id="86bc8-125">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="86bc8-126">Yineleyici işlevi her çağrısı devam eder, sonraki yürütülmesi `Yield` sonraki yinelemesini sırasında oluşur deyimi `For…Next` döngü.</span><span class="sxs-lookup"><span data-stu-id="86bc8-126">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="86bc8-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="86bc8-127">Example</span></span>  
 <span data-ttu-id="86bc8-128">Aşağıdaki örnekte gösterilmiştir bir `Get` yineleyici olduğu erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="86bc8-128">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="86bc8-129">`Iterator` Değiştirici özelliği bildiriminde olduğu.</span><span class="sxs-lookup"><span data-stu-id="86bc8-129">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 <span data-ttu-id="86bc8-130">Ek örnekler için bkz: [yineleyiciler](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="86bc8-130">For additional examples, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86bc8-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86bc8-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [<span data-ttu-id="86bc8-132">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="86bc8-132">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="86bc8-133">Yield deyimi</span><span class="sxs-lookup"><span data-stu-id="86bc8-133">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
