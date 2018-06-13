---
title: Yineleyici (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 565508046b3fa2dc52acf8c5204153beffc15d9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599518"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="ab4bb-102">Yineleyici (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab4bb-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="ab4bb-103">Belirleyen bir işlevi veya `Get` erişimci yineleyici olduğu.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab4bb-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab4bb-104">Remarks</span></span>  
 <span data-ttu-id="ab4bb-105">Bir *yineleyici* özel bir yineleme içinde bir koleksiyon gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="ab4bb-106">Yineleyici kullanan [verim](../../../visual-basic/language-reference/statements/yield-statement.md) deyimi koleksiyondaki bir birer birer her öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="ab4bb-107">Zaman bir `Yield` deyimi ulaşıldığında, kod geçerli konumda korunur.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="ab4bb-108">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="ab4bb-109">Yineleyici bir işlevi veya olarak uygulanabileceği bir `Get` özelliği tanımı erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="ab4bb-110">`Iterator` Değiştiricisi görünür yineleyici işlevi bildiriminde veya `Get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="ab4bb-111">Yineleyici kullanarak istemci kodundan çağıran bir [For Each... Sonraki deyim](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ab4bb-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="ab4bb-112">Bir yineleyici işlevinin dönüş türü veya `Get` erişimci olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="ab4bb-113">Yineleyici içeremez `ByRef` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="ab4bb-114">Yineleyici bir olay, örnek oluşturucusu, statik Oluşturucusu veya statik yıkıcı gerçekleşemez.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="ab4bb-115">Yineleyici adsız bir işlev olabilir.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="ab4bb-116">Daha fazla bilgi için bkz: [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="ab4bb-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="ab4bb-117">Kullanım</span><span class="sxs-lookup"><span data-stu-id="ab4bb-117">Usage</span></span>  
 <span data-ttu-id="ab4bb-118">`Iterator` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ab4bb-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="ab4bb-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab4bb-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="ab4bb-120">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab4bb-120">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="ab4bb-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab4bb-121">Example</span></span>  
 <span data-ttu-id="ab4bb-122">Aşağıdaki örnek, bir yineleyici işlevi gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="ab4bb-123">Yineleyici işlevinin bir `Yield` içinde deyimi bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="ab4bb-124">Her yinelemesinden [her](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyiminin gövdesinde `Main` yapılan bir çağrı oluşturur `Power` yineleyici işlevi.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="ab4bb-125">Yineleyici işlevi her çağrısı devam eder, sonraki yürütülmesi `Yield` sonraki yinelemesini sırasında oluşur deyimi `For…Next` döngü.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="ab4bb-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab4bb-126">Example</span></span>  
 <span data-ttu-id="ab4bb-127">Aşağıdaki örnekte gösterilmiştir bir `Get` yineleyici olduğu erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="ab4bb-128">`Iterator` Değiştirici özelliği bildiriminde olduğu.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 <span data-ttu-id="ab4bb-129">Ek örnekler için bkz: [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="ab4bb-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab4bb-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab4bb-130">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [<span data-ttu-id="ab4bb-131">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="ab4bb-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)  
 [<span data-ttu-id="ab4bb-132">Yield Deyimi</span><span class="sxs-lookup"><span data-stu-id="ab4bb-132">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
