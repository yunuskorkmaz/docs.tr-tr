---
title: Yield Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 72a8dafdc5aa834a644e1e70a309cfc0827b5fdf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352720"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="dbe25-102">Yield Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbe25-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="dbe25-103">Bir koleksiyonun Next öğesini bir `For Each...Next` ifadesine gönderir.</span><span class="sxs-lookup"><span data-stu-id="dbe25-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe25-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbe25-104">Syntax</span></span>  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbe25-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dbe25-105">Parameters</span></span>  
  
|<span data-ttu-id="dbe25-106">Terim</span><span class="sxs-lookup"><span data-stu-id="dbe25-106">Term</span></span>|<span data-ttu-id="dbe25-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="dbe25-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="dbe25-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="dbe25-108">Required.</span></span> <span data-ttu-id="dbe25-109">Yineleyici işlevinin türüne örtülü olarak dönüştürülebilir bir ifade veya `Yield` deyimini içeren `Get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="dbe25-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbe25-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dbe25-110">Remarks</span></span>  
 <span data-ttu-id="dbe25-111">`Yield` deyimin her seferinde bir koleksiyonun bir öğesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="dbe25-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="dbe25-112">`Yield` deyimin bir yineleyici işlevi veya bir koleksiyon üzerinde özel yinelemeler gerçekleştiren `Get` erişimcisi vardır.</span><span class="sxs-lookup"><span data-stu-id="dbe25-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="dbe25-113">For each ile bir yineleyici işlevi kullanıyorsunuz [... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-each-next-statement.md) veya BIR LINQ sorgusu.</span><span class="sxs-lookup"><span data-stu-id="dbe25-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="dbe25-114">`For Each` döngüsünün her yinelemesi yineleyici işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="dbe25-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="dbe25-115">Yineleyici işlevinde bir `Yield` ifadesine ulaşıldığında, `expression` döndürülür ve koddaki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="dbe25-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="dbe25-116">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="dbe25-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="dbe25-117">Örtük bir dönüştürme, `Yield` deyimindeki `expression` türünün, yineleyicinin dönüş türüne sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbe25-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="dbe25-118">Yinelemeyi sonlandırmak için bir `Exit Function` veya `Return` ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbe25-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="dbe25-119">"Yield" ayrılmış bir sözcük değildir ve yalnızca bir `Iterator` işlevinde veya `Get` erişimcisinde kullanıldığında özel anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="dbe25-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="dbe25-120">Yineleyici işlevleri ve `Get` erişimcileri hakkında daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="dbe25-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="dbe25-121">Yineleyici Işlevleri ve get erişimcileri</span><span class="sxs-lookup"><span data-stu-id="dbe25-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="dbe25-122">Yineleyici işlev veya `Get` erişimcisinin bildirimi aşağıdaki gereksinimleri karşılamalıdır:</span><span class="sxs-lookup"><span data-stu-id="dbe25-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
- <span data-ttu-id="dbe25-123">[Yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md) değiştiricisi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="dbe25-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
- <span data-ttu-id="dbe25-124">Dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>veya <xref:System.Collections.Generic.IEnumerator%601>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dbe25-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
- <span data-ttu-id="dbe25-125">`ByRef` parametreye sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="dbe25-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="dbe25-126">Bir olay, örnek Oluşturucu, statik oluşturucu veya statik yok edicisi içinde Yineleyici işlevi oluşamaz.</span><span class="sxs-lookup"><span data-stu-id="dbe25-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="dbe25-127">Yineleyici işlevi anonim bir işlev olabilir.</span><span class="sxs-lookup"><span data-stu-id="dbe25-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="dbe25-128">Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="dbe25-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="dbe25-129">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="dbe25-129">Exception Handling</span></span>  
 <span data-ttu-id="dbe25-130">`Yield` bir ifade, TRY `Try` bloğunun içinde olabilir [... Yakala... Finally ekstresi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="dbe25-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="dbe25-131">`Yield` bildirimine sahip bir `Try` bloğunda `Catch` blokları olabilir ve bir `Finally` bloğuna sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="dbe25-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="dbe25-132">`Yield` bir ifade `Catch` bloğunun veya `Finally` bloğunun içinde olamaz.</span><span class="sxs-lookup"><span data-stu-id="dbe25-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="dbe25-133">`For Each` gövdesi (Yineleyici işlevi dışında) bir özel durum oluşturursa, yineleyici işlevindeki bir `Catch` bloğu yürütülmez, ancak Yineleyici işlevindeki bir `Finally` bloğu yürütülür.</span><span class="sxs-lookup"><span data-stu-id="dbe25-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="dbe25-134">Yineleyici işlevi içindeki bir `Catch` bloğu yalnızca Yineleyici işlevinin içinde oluşan özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="dbe25-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="dbe25-135">Teknik Uygulama</span><span class="sxs-lookup"><span data-stu-id="dbe25-135">Technical Implementation</span></span>  
 <span data-ttu-id="dbe25-136">Aşağıdaki kod bir yineleyici işlevinden `IEnumerable (Of String)` döndürür ve sonra `IEnumerable (Of String)`öğeleri boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="dbe25-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="dbe25-137">`MyIteratorFunction` çağrısı işlevin gövdesini yürütmez.</span><span class="sxs-lookup"><span data-stu-id="dbe25-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="dbe25-138">Bunun yerine, çağrı `elements` değişkenine bir `IEnumerable(Of String)` döndürür.</span><span class="sxs-lookup"><span data-stu-id="dbe25-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="dbe25-139">`For Each` döngüsünün bir yinelemesi üzerinde `elements`için <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="dbe25-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="dbe25-140">Bu çağrı, sonraki `Yield` ifadesine ulaşılana kadar `MyIteratorFunction` gövdesini yürütür.</span><span class="sxs-lookup"><span data-stu-id="dbe25-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="dbe25-141">`Yield` deyimi, yalnızca döngü gövdesine göre tüketim için `element` değişkeninin değerini değil, aynı zamanda bir `IEnumerable (Of String)`olan öğelerin <xref:System.Collections.Generic.IEnumerator%601.Current%2A> özelliğini de belirleyen bir ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="dbe25-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="dbe25-142">`For Each` döngüsünün sonraki tekrarında, yineleyici gövdesinin yürütülmesi kaldığınız yerden devam eder, bir `Yield` bildirimine ulaştığında yeniden durdurulur.</span><span class="sxs-lookup"><span data-stu-id="dbe25-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="dbe25-143">Yineleyici işlevinin sonuna veya bir `Return` ya da `Exit Function` ifadeye ulaşıldığında `For Each` döngüsü tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="dbe25-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbe25-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbe25-144">Example</span></span>  
 <span data-ttu-id="dbe25-145">Aşağıdaki örnek, Için içinde olan bir `Yield` ifadeye sahiptir [... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="dbe25-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="dbe25-146">`Main` [for each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyimlerinin her yinelemesi, `Power` Yineleyici işlevine bir çağrı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbe25-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="dbe25-147">Yineleyici işlevine yapılan her çağrı, `For…Next` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan `Yield` deyimin bir sonraki yürütmeye ilerler.</span><span class="sxs-lookup"><span data-stu-id="dbe25-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="dbe25-148">Yineleyici yönteminin dönüş türü, bir Yineleyici arabirimi türü <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="dbe25-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="dbe25-149">Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="dbe25-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="dbe25-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbe25-150">Example</span></span>  
 <span data-ttu-id="dbe25-151">Aşağıdaki örnek, yineleyici olan bir `Get` erişimcisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbe25-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="dbe25-152">Özellik bildirimi `Iterator` değiştirici içerir.</span><span class="sxs-lookup"><span data-stu-id="dbe25-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="dbe25-153">Ek örnekler için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="dbe25-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe25-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbe25-154">See also</span></span>

- [<span data-ttu-id="dbe25-155">Deyimler</span><span class="sxs-lookup"><span data-stu-id="dbe25-155">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
