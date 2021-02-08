---
description: 'Daha fazla bilgi edinin: yield ekstresi (Visual Basic)'
title: Yield Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: cd07c271722a715beeddfddf660cec3e05127db8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787558"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="6cb78-103">Yield Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cb78-103">Yield Statement (Visual Basic)</span></span>

<span data-ttu-id="6cb78-104">Bir koleksiyonun Next öğesini bir `For Each...Next` ifadeye gönderir.</span><span class="sxs-lookup"><span data-stu-id="6cb78-104">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cb78-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6cb78-105">Syntax</span></span>  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cb78-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6cb78-106">Parameters</span></span>  
  
|<span data-ttu-id="6cb78-107">Süre</span><span class="sxs-lookup"><span data-stu-id="6cb78-107">Term</span></span>|<span data-ttu-id="6cb78-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="6cb78-108">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="6cb78-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6cb78-109">Required.</span></span> <span data-ttu-id="6cb78-110">İfadeyi içeren yineleyici işlevin veya erişimcinin türüne örtülü olarak dönüştürülebilir bir ifade `Get` `Yield` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-110">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cb78-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6cb78-111">Remarks</span></span>  

 <span data-ttu-id="6cb78-112">`Yield`İfade, aynı anda bir koleksiyonun bir öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6cb78-112">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="6cb78-113">`Yield`İfade, `Get` bir koleksiyon üzerinde özel yinelemeler gerçekleştiren bir Yineleyici işlevine veya erişimciye dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6cb78-113">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="6cb78-114">For each ile bir yineleyici işlevi kullanıyorsunuz [... Sonraki Ifade](for-each-next-statement.md) veya BIR LINQ sorgusu.</span><span class="sxs-lookup"><span data-stu-id="6cb78-114">You consume an iterator function by using a [For Each...Next Statement](for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="6cb78-115">Döngünün her yinelemesi `For Each` yineleyici işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="6cb78-115">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="6cb78-116">`Yield`Yineleyici işlevinde bir ifadeye ulaşıldığında, `expression` döndürülür ve koddaki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="6cb78-116">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="6cb78-117">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="6cb78-117">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="6cb78-118">Örtük dönüştürme, `expression` `Yield` deyimdeki türünden yineleyicinin dönüş türüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6cb78-118">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="6cb78-119">`Exit Function` `Return` Yinelemeyi sonlandırmak için bir veya ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cb78-119">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="6cb78-120">"Yield" ayrılmış bir sözcük değildir ve yalnızca bir `Iterator` işlevde veya erişimcisinde kullanıldığında özel anlamı vardır `Get` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-120">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="6cb78-121">Yineleyici işlevleri ve erişimcileri hakkında daha fazla bilgi için `Get` bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="6cb78-121">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="6cb78-122">Yineleyici Işlevleri ve get erişimcileri</span><span class="sxs-lookup"><span data-stu-id="6cb78-122">Iterator Functions and Get Accessors</span></span>  

 <span data-ttu-id="6cb78-123">Yineleyici işlev veya `Get` erişimcinin bildirimi aşağıdaki gereksinimleri karşılamalıdır:</span><span class="sxs-lookup"><span data-stu-id="6cb78-123">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
- <span data-ttu-id="6cb78-124">[Yineleyici](../modifiers/iterator.md) değiştiricisi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="6cb78-124">It must include an [Iterator](../modifiers/iterator.md) modifier.</span></span>  
  
- <span data-ttu-id="6cb78-125">Dönüş türü <xref:System.Collections.IEnumerable> ,, veya olmalıdır <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="6cb78-125">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
- <span data-ttu-id="6cb78-126">Herhangi bir parametreye sahip olamaz `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-126">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="6cb78-127">Bir olay, örnek Oluşturucu, statik oluşturucu veya statik yok edicisi içinde Yineleyici işlevi oluşamaz.</span><span class="sxs-lookup"><span data-stu-id="6cb78-127">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="6cb78-128">Yineleyici işlevi anonim bir işlev olabilir.</span><span class="sxs-lookup"><span data-stu-id="6cb78-128">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="6cb78-129">Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="6cb78-129">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="6cb78-130">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="6cb78-130">Exception Handling</span></span>  

 <span data-ttu-id="6cb78-131">Bir `Yield` ifade bir `Try` try bloğunun içinde olabilir [... Yakala... Finally ekstresi](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6cb78-131">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span> <span data-ttu-id="6cb78-132">`Try`Bir deyime sahip bir blok `Yield` blokları olabilir `Catch` ve bir bloğuna sahip olabilir `Finally` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-132">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="6cb78-133">Bir `Yield` ifade bir `Catch` blok veya blok içinde olamaz `Finally` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-133">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="6cb78-134">`For Each`Gövde (Yineleyici işlevi dışında) bir özel durum oluşturursa, `Catch` Yineleyici işlevindeki bir blok yürütülmez, ancak `Finally` Yineleyici işlevindeki bir blok yürütülür.</span><span class="sxs-lookup"><span data-stu-id="6cb78-134">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="6cb78-135">`Catch`Yineleyici işlevi içindeki bir blok yalnızca Yineleyici işlevinin içinde oluşan özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="6cb78-135">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="6cb78-136">Teknik Uygulama</span><span class="sxs-lookup"><span data-stu-id="6cb78-136">Technical Implementation</span></span>  

 <span data-ttu-id="6cb78-137">Aşağıdaki kod bir `IEnumerable (Of String)` Yineleyici işlevinden bir döndürür ve sonra öğelerinin öğeleri boyunca yinelenir `IEnumerable (Of String)` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-137">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="6cb78-138">Çağrısı, `MyIteratorFunction` işlevinin gövdesini yürütmez.</span><span class="sxs-lookup"><span data-stu-id="6cb78-138">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="6cb78-139">Bunun yerine, çağrı `IEnumerable(Of String)` değişkenine bir döndürür `elements` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-139">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="6cb78-140">Döngüsünün bir yinelemesinde `For Each` , <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için çağrılır `elements` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-140">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="6cb78-141">Bu çağrı, `MyIteratorFunction` sonraki `Yield` ifadeye ulaşılana kadar gövdesini yürütür.</span><span class="sxs-lookup"><span data-stu-id="6cb78-141">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="6cb78-142">`Yield`Deyimi, `element` döngü gövdesi tarafından tüketim için değişkenin değerini değil, aynı zamanda bir olan öğelerin özelliğini de belirleyen bir ifade döndürür <xref:System.Collections.Generic.IEnumerator%601.Current%2A> `IEnumerable (Of String)` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-142">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="6cb78-143">Döngünün sonraki tekrarında `For Each` , yineleyici gövdesinin yürütülmesi kaldığınız yerden devam eder, bir ifadeye ulaştığında yeniden durdurulur `Yield` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-143">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="6cb78-144">`For Each`Döngü, Yineleyici işlevinin veya `Return` or ifadesinin sonuna ulaşıldığında tamamlanır `Exit Function` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-144">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cb78-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cb78-145">Example</span></span>  

 <span data-ttu-id="6cb78-146">Aşağıdaki örnek, `Yield` için içinde olan bir ifadeye sahiptir [... Sonraki](for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="6cb78-146">The following example has a `Yield` statement that is inside a [For…Next](for-next-statement.md) loop.</span></span> <span data-ttu-id="6cb78-147">İçindeki [her bir for](for-each-next-statement.md) Ifadesinin gövdesi için her yineleme, `Main` Yineleyici işlevine bir çağrı oluşturur `Power` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-147">Each iteration of the [For Each](for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="6cb78-148">Yineleyici işlevine yapılan her çağrı, `Yield` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan deyimin bir sonraki yürütmeye ilerler `For…Next` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-148">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="6cb78-149">Yineleyici yönteminin dönüş türü <xref:System.Collections.Generic.IEnumerable%601> , bir Yineleyici arabirimi türüdür.</span><span class="sxs-lookup"><span data-stu-id="6cb78-149">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="6cb78-150">Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="6cb78-150">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="6cb78-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cb78-151">Example</span></span>  

 <span data-ttu-id="6cb78-152">Aşağıdaki örnek, `Get` Yineleyici olan bir erişimciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6cb78-152">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="6cb78-153">Özellik bildirimi bir değiştirici içerir `Iterator` .</span><span class="sxs-lookup"><span data-stu-id="6cb78-153">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="6cb78-154">Ek örnekler için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="6cb78-154">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb78-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cb78-155">See also</span></span>

- [<span data-ttu-id="6cb78-156">Deyimler</span><span class="sxs-lookup"><span data-stu-id="6cb78-156">Statements</span></span>](index.md)
