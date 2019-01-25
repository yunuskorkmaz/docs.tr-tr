---
title: Yield Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: da01d3f1bdfa3e76afcc28e7b70240beb06f74f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506491"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="e7682-102">Yield Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7682-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="e7682-103">Bir koleksiyona sonraki öğeye gönderen bir `For Each...Next` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e7682-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7682-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7682-104">Syntax</span></span>  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7682-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7682-105">Parameters</span></span>  
  
|<span data-ttu-id="e7682-106">Terim</span><span class="sxs-lookup"><span data-stu-id="e7682-106">Term</span></span>|<span data-ttu-id="e7682-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="e7682-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="e7682-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e7682-108">Required.</span></span> <span data-ttu-id="e7682-109">Yineleyici işleve türüne örtük olarak dönüştürülebilir bir ifade veya `Get` içeren erişimci `Yield` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e7682-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7682-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7682-110">Remarks</span></span>  
 <span data-ttu-id="e7682-111">`Yield` Deyimi aynı anda bir koleksiyonun bir öğesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="e7682-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="e7682-112">`Yield` Deyimi bir yineleyici işlevinde dahil veya `Get` form veya erişimci bir koleksiyon üzerinde özel yineleme gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="e7682-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="e7682-113">Kullanarak bir yineleyici işlevi tükettiğiniz bir [her biri için... Sonraki deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md) veya LINQ sorgusu.</span><span class="sxs-lookup"><span data-stu-id="e7682-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="e7682-114">Her bir yinelemesini `For Each` döngüsü yineleyici işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="e7682-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="e7682-115">Olduğunda bir `Yield` yineleyici işlevinde deyimine ulaşıldığında `expression` döndürülür ve kodun geçerli konumu korunur.</span><span class="sxs-lookup"><span data-stu-id="e7682-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="e7682-116">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="e7682-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="e7682-117">Örtük bir dönüştürme türünden bulunmalıdır `expression` içinde `Yield` deyimi için dönüş türü yineleyici.</span><span class="sxs-lookup"><span data-stu-id="e7682-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="e7682-118">Kullanabileceğiniz bir `Exit Function` veya `Return` yinelemeyi sonlandırmak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="e7682-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="e7682-119">"Yield" ayrılmış bir sözcük değildir ve yalnızca içinde kullanıldığında özel anlamı bir `Iterator` işlevi veya `Get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="e7682-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="e7682-120">Yineleyici işlevleri hakkında daha fazla bilgi ve `Get` erişimcileri bkz [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="e7682-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="e7682-121">Yineleyici işlevleri ve Get erişimcileri</span><span class="sxs-lookup"><span data-stu-id="e7682-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="e7682-122">Bir yineleyici işlevin bildirimi ya da `Get` erişimci aşağıdaki gereksinimleri karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="e7682-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="e7682-123">Bunu içermelidir bir [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="e7682-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
-   <span data-ttu-id="e7682-124">Dönüş türü olmalıdır <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="e7682-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="e7682-125">Bunu içeremez `ByRef` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="e7682-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="e7682-126">Bir yineleyici işlevine bir olay, örnek oluşturucusu, statik oluşturucu veya statik yok Edicisi olamaz.</span><span class="sxs-lookup"><span data-stu-id="e7682-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="e7682-127">Bir yineleyici işlevi anonim bir işlevdir olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7682-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="e7682-128">Daha fazla bilgi için [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="e7682-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="e7682-129">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="e7682-129">Exception Handling</span></span>  
 <span data-ttu-id="e7682-130">A `Yield` deyimi içinde olabilir bir `Try` bloğu bir [deneyin... Catch... Finally deyimini](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e7682-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="e7682-131">A `Try` sahip blok bir `Yield` deyimi olabilir `Catch` engeller ve olabilir bir `Finally` blok.</span><span class="sxs-lookup"><span data-stu-id="e7682-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="e7682-132">A `Yield` deyimi içinde olamaz bir `Catch` blok veya `Finally` blok.</span><span class="sxs-lookup"><span data-stu-id="e7682-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="e7682-133">Varsa `For Each` gövdesi (yineleyici işleve dışında) bir özel durum oluşturursa bir `Catch` yineleyici işleve bloğunda yürütülmedi, ancak bir `Finally` yineleyici işleve bloğunda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="e7682-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="e7682-134">A `Catch` blok içinde bir yineleyici işlevi yineleyici işlevde oluşan özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="e7682-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="e7682-135">Teknik Uygulama</span><span class="sxs-lookup"><span data-stu-id="e7682-135">Technical Implementation</span></span>  
 <span data-ttu-id="e7682-136">Aşağıdaki kod döndürür bir `IEnumerable (Of String)` yineleyici işlevi ve ardından öğeleri yinelenir `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="e7682-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="e7682-137">Çağrı `MyIteratorFunction` işlev gövdesini yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e7682-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="e7682-138">Bunun yerine çağrı döndürür bir `IEnumerable(Of String)` içine `elements` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="e7682-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="e7682-139">Yinelemesi üzerinde `For Each` döngü <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için çağrılır `elements`.</span><span class="sxs-lookup"><span data-stu-id="e7682-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="e7682-140">Bu çağrı gövdesini yürütür `MyIteratorFunction` sonraki kadar `Yield` deyimine ulaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="e7682-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="e7682-141">`Yield` Deyimi yalnızca değerini belirleyen bir ifade döndürür `element` döngü gövdesinin tüketimi için değişken aynı zamanda <xref:System.Collections.Generic.IEnumerator%601.Current%2A> olan özellik öğelerinin bir `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="e7682-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="e7682-142">Her yinelemesinde `For Each` kadar yineleyici gövdenin yürütülmesi devam eder, döngü onu ulaştığında yeniden kaldığı bir `Yield` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e7682-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="e7682-143">`For Each` Tamamlandıktan döngüsü yineleyici işlevin sonuna veya bir `Return` veya `Exit Function` deyimine ulaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="e7682-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7682-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7682-144">Example</span></span>  
 <span data-ttu-id="e7682-145">Aşağıdaki örnek sahip bir `Yield` içindeki bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="e7682-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="e7682-146">Her bir yinelemesini [her](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyiminin gövdesinde `Main` bir çağrı oluşturur `Power` yineleyici işlevi.</span><span class="sxs-lookup"><span data-stu-id="e7682-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="e7682-147">Her yineleyici işleve çağrı için sonraki yürütme devam eder `Yield` sıradaki yinelemesi süresince gerçekleşen deyimi `For…Next` döngü.</span><span class="sxs-lookup"><span data-stu-id="e7682-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="e7682-148">Yineleyici yöntemin dönüş türü <xref:System.Collections.Generic.IEnumerable%601>, bir yineleyici arabirimi türü.</span><span class="sxs-lookup"><span data-stu-id="e7682-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="e7682-149">Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="e7682-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="e7682-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7682-150">Example</span></span>  
 <span data-ttu-id="e7682-151">Aşağıdaki örnek, gösterir bir `Get` bir yineleyici erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="e7682-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="e7682-152">Özellik bildirimi içeren bir `Iterator` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="e7682-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 <span data-ttu-id="e7682-153">Diğer örnekler için [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="e7682-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7682-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7682-154">See also</span></span>
- [<span data-ttu-id="e7682-155">Deyimler</span><span class="sxs-lookup"><span data-stu-id="e7682-155">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
