---
title: Yineleyici
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 9d7eaf186bae544031487ce027505e1e0d4ae0f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351531"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="1ef18-102">Yineleyici (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ef18-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="1ef18-103">Bir işlev veya `Get` erişimcisinin bir yineleyici olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ef18-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ef18-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ef18-104">Remarks</span></span>  
 <span data-ttu-id="1ef18-105">*Yineleyici* bir koleksiyon üzerinde özel bir yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1ef18-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="1ef18-106">Bir yineleyici, koleksiyondaki her öğeyi tek seferde döndürmek için [yield](../../../visual-basic/language-reference/statements/yield-statement.md) ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ef18-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="1ef18-107">`Yield` ifadeye ulaşıldığında, koddaki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="1ef18-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="1ef18-108">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="1ef18-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="1ef18-109">Yineleyici, bir işlev olarak veya bir özellik tanımının `Get` erişimcisi olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1ef18-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="1ef18-110">`Iterator` değiştiricisi yineleyici işlevin veya `Get` erişimcisinin bildiriminde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1ef18-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="1ef18-111">Her biri Için bir kullanarak istemci kodundan bir yineleyici çağırın [... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1ef18-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="1ef18-112">Yineleyici işlev veya `Get` erişimcisinin dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>veya <xref:System.Collections.Generic.IEnumerator%601>olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ef18-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="1ef18-113">Bir yineleyici `ByRef` parametreye sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="1ef18-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="1ef18-114">Bir olay, örnek Oluşturucu, statik oluşturucu veya statik yok edicisi içinde yineleyici olamaz.</span><span class="sxs-lookup"><span data-stu-id="1ef18-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="1ef18-115">Yineleyici bir anonim işlev olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ef18-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="1ef18-116">Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="1ef18-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="1ef18-117">Kullanım</span><span class="sxs-lookup"><span data-stu-id="1ef18-117">Usage</span></span>  
 <span data-ttu-id="1ef18-118">`Iterator` değiştiricisi şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1ef18-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="1ef18-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="1ef18-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="1ef18-120">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="1ef18-120">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="1ef18-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ef18-121">Example</span></span>  
 <span data-ttu-id="1ef18-122">Aşağıdaki örnekte bir yineleyici işlevi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ef18-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="1ef18-123">Yineleyici işlevi Için bir for... içinde olan bir `Yield` ifadeye sahip [... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="1ef18-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="1ef18-124">`Main` [for each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyimlerinin her yinelemesi, `Power` Yineleyici işlevine bir çağrı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ef18-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="1ef18-125">Yineleyici işlevine yapılan her çağrı, `For…Next` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan `Yield` deyimin bir sonraki yürütmeye ilerler.</span><span class="sxs-lookup"><span data-stu-id="1ef18-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="1ef18-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ef18-126">Example</span></span>  
 <span data-ttu-id="1ef18-127">Aşağıdaki örnek, yineleyici olan bir `Get` erişimcisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ef18-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="1ef18-128">`Iterator` değiştiricisi özellik bildiriminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1ef18-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="1ef18-129">Ek örnekler için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="1ef18-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef18-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ef18-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="1ef18-131">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="1ef18-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="1ef18-132">Yield Deyimi</span><span class="sxs-lookup"><span data-stu-id="1ef18-132">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
