---
title: Iterator
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: bb19289c69f4c523363e88e91a58f37d232b07df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396239"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="cac56-102">Yineleyici (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cac56-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="cac56-103">Bir işlevin veya `Get` erişimcinin bir yineleyici olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cac56-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cac56-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cac56-104">Remarks</span></span>  
 <span data-ttu-id="cac56-105">*Yineleyici* bir koleksiyon üzerinde özel bir yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="cac56-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="cac56-106">Bir yineleyici, koleksiyondaki her öğeyi tek seferde döndürmek için [yield](../statements/yield-statement.md) ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cac56-106">An iterator uses the [Yield](../statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="cac56-107">Bir `Yield` ifadeye ulaşıldığında, koddaki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="cac56-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="cac56-108">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="cac56-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="cac56-109">Yineleyici, bir işlev olarak veya bir `Get` özellik tanımının erişimcisi olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="cac56-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="cac56-110">`Iterator`Değiştirici, Yineleyici işlevinin veya `Get` erişimcinin bildiriminde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cac56-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="cac56-111">Her biri Için bir kullanarak istemci kodundan bir yineleyici çağırın [... Sonraki Ifade](../statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cac56-111">You call an iterator from client code by using a [For Each...Next Statement](../statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="cac56-112">Yineleyici işlevinin veya `Get` erişimcisinin dönüş türü <xref:System.Collections.IEnumerable> ,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> , veya olabilir <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="cac56-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="cac56-113">Yineleyicinin herhangi bir `ByRef` parametresi olamaz.</span><span class="sxs-lookup"><span data-stu-id="cac56-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="cac56-114">Bir olay, örnek Oluşturucu, statik oluşturucu veya statik yok edicisi içinde yineleyici olamaz.</span><span class="sxs-lookup"><span data-stu-id="cac56-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="cac56-115">Yineleyici bir anonim işlev olabilir.</span><span class="sxs-lookup"><span data-stu-id="cac56-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="cac56-116">Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="cac56-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="cac56-117">Kullanım</span><span class="sxs-lookup"><span data-stu-id="cac56-117">Usage</span></span>  
 <span data-ttu-id="cac56-118">`Iterator`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="cac56-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="cac56-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="cac56-119">Function Statement</span></span>](../statements/function-statement.md)  
  
- [<span data-ttu-id="cac56-120">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="cac56-120">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="cac56-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="cac56-121">Example</span></span>  
 <span data-ttu-id="cac56-122">Aşağıdaki örnekte bir yineleyici işlevi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cac56-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="cac56-123">Yineleyici işlevinin, `Yield` için içindeki bir ifade vardır [... Sonraki](../statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="cac56-123">The iterator function has a `Yield` statement that is inside a [For…Next](../statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="cac56-124">İçindeki [her bir for](../statements/for-each-next-statement.md) Ifadesinin gövdesi için her yineleme, `Main` Yineleyici işlevine bir çağrı oluşturur `Power` .</span><span class="sxs-lookup"><span data-stu-id="cac56-124">Each iteration of the [For Each](../statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="cac56-125">Yineleyici işlevine yapılan her çağrı, `Yield` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan deyimin bir sonraki yürütmeye ilerler `For…Next` .</span><span class="sxs-lookup"><span data-stu-id="cac56-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="cac56-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="cac56-126">Example</span></span>  
 <span data-ttu-id="cac56-127">Aşağıdaki örnek, `Get` Yineleyici olan bir erişimciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="cac56-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="cac56-128">`Iterator`Değiştirici, özellik bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="cac56-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="cac56-129">Ek örnekler için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="cac56-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac56-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cac56-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="cac56-131">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="cac56-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="cac56-132">Yield Deyimi</span><span class="sxs-lookup"><span data-stu-id="cac56-132">Yield Statement</span></span>](../statements/yield-statement.md)
