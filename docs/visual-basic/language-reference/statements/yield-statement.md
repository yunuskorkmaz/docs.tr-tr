---
title: Yield Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0bc2f5c2dca1fbd6039f10ddd6204673f60a679d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="4a955-102">Yield Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a955-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="4a955-103">Bir koleksiyona sonraki öğeye gönderir bir `For Each...Next` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4a955-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a955-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a955-104">Syntax</span></span>  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a955-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a955-105">Parameters</span></span>  
  
|<span data-ttu-id="4a955-106">Terim</span><span class="sxs-lookup"><span data-stu-id="4a955-106">Term</span></span>|<span data-ttu-id="4a955-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="4a955-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="4a955-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4a955-108">Required.</span></span> <span data-ttu-id="4a955-109">Yineleyici işlevi türüne örtük olarak dönüştürülebilir bir deyim veya `Get` içeren erişimcisi `Yield` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4a955-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a955-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a955-110">Remarks</span></span>  
 <span data-ttu-id="4a955-111">`Yield` Deyimi bir seferde bir koleksiyonun bir öğesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="4a955-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="4a955-112">`Yield` Deyimi bir yineleyici işlevinde dahil veya `Get` içinde bir koleksiyon özel yineleme gerçekleştirmek erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="4a955-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="4a955-113">İle bir yineleyici işlevi kullanmasını bir [For Each... Sonraki deyim](../../../visual-basic/language-reference/statements/for-each-next-statement.md) veya bir LINQ Sorgu.</span><span class="sxs-lookup"><span data-stu-id="4a955-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="4a955-114">Her yinelemesinden `For Each` döngü yineleyici işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="4a955-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="4a955-115">Zaman bir `Yield` deyimi yineleyici işlevinde ulaşıldığında `expression` döndürülür ve kod geçerli konumda korunur.</span><span class="sxs-lookup"><span data-stu-id="4a955-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="4a955-116">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="4a955-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="4a955-117">Örtük bir dönüştürme türünden bulunmalıdır `expression` içinde `Yield` yineleyici dönüş türü bildirimi.</span><span class="sxs-lookup"><span data-stu-id="4a955-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="4a955-118">Kullanabileceğiniz bir `Exit Function` veya `Return` yinelemeyi sonlandırmak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="4a955-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="4a955-119">"Verim" ayrılmış bir sözcük değildir ve yalnızca içinde kullanıldığında, özel bir anlamı olan bir `Iterator` işlevi veya `Get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="4a955-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="4a955-120">Yineleyici işlevleri hakkında daha fazla bilgi için ve `Get` erişimciler, bkz: [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="4a955-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="4a955-121">Yineleyici işlevleri ve Get erişimcisi</span><span class="sxs-lookup"><span data-stu-id="4a955-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="4a955-122">Yineleyici işlevin bildirimi veya `Get` erişimci aşağıdaki gereksinimleri karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="4a955-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="4a955-123">İçermesi gerekir bir [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="4a955-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
-   <span data-ttu-id="4a955-124">Dönüş türü olmalıdır <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="4a955-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="4a955-125">Bunu içeremez `ByRef` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="4a955-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="4a955-126">Yineleyici işlevi, bir olay, örnek oluşturucusu, statik Oluşturucusu veya statik yıkıcı gerçekleşemez.</span><span class="sxs-lookup"><span data-stu-id="4a955-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="4a955-127">Yineleyici işlevi adsız bir işlev olabilir.</span><span class="sxs-lookup"><span data-stu-id="4a955-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="4a955-128">Daha fazla bilgi için bkz: [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="4a955-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="4a955-129">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="4a955-129">Exception Handling</span></span>  
 <span data-ttu-id="4a955-130">A `Yield` deyimi içinde bulunabilir bir `Try` , engelleme bir [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4a955-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="4a955-131">A `Try` sahip blok bir `Yield` deyimi olabilir `Catch` engeller ve olabilir bir `Finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="4a955-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="4a955-132">A `Yield` deyimi içinde olamaz bir `Catch` blok veya `Finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="4a955-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="4a955-133">Varsa `For Each` gövdesi (dışında yineleyici işlevi) bir özel durum oluşturur bir `Catch` yineleyici işlevi bloğunda yürütülmez, ancak bir `Finally` yineleyici işlevi bloğunda gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4a955-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="4a955-134">A `Catch` yineleyici işlevi bloğunda yineleyici işlevinin içinde oluşan özel durumlarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="4a955-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="4a955-135">Teknik Uygulama</span><span class="sxs-lookup"><span data-stu-id="4a955-135">Technical Implementation</span></span>  
 <span data-ttu-id="4a955-136">Aşağıdaki kod döndürür bir `IEnumerable (Of String)` yineleyici işlevden ve öğelerinde yineleme `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="4a955-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="4a955-137">Çağrı `MyIteratorFunction` işlevinin gövdesini yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4a955-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="4a955-138">Bunun yerine çağrı döndürür bir `IEnumerable(Of String)` içine `elements` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4a955-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="4a955-139">Bir yineleme `For Each` döngü, <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için çağrılır `elements`.</span><span class="sxs-lookup"><span data-stu-id="4a955-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="4a955-140">Bu çağrı gövdesini yürütür `MyIteratorFunction` sonraki kadar `Yield` deyimi ulaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="4a955-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="4a955-141">`Yield` Deyimi yalnızca değerini belirleyen bir ifade döndürür `element` döngü gövdesine tüketimi için değişken aynı zamanda <xref:System.Collections.Generic.IEnumerator%601.Current%2A> olan özelliği öğelerinin bir `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="4a955-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="4a955-142">Sonraki her yinelemesinden üzerinde `For Each` nereden yürütülmeye yineleyici gövdesinin döngü ulaştığında yeniden durdurma kapalı, solda bir `Yield` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4a955-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="4a955-143">`For Each` Döngüsü tamamlandıktan yineleyici işlevi sonuna veya `Return` veya `Exit Function` deyimi ulaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="4a955-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a955-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a955-144">Example</span></span>  
 <span data-ttu-id="4a955-145">Aşağıdaki örnek sahip bir `Yield` içinde deyimi bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="4a955-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="4a955-146">Her yinelemesinden [her](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyiminin gövdesinde `Main` yapılan bir çağrı oluşturur `Power` yineleyici işlevi.</span><span class="sxs-lookup"><span data-stu-id="4a955-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="4a955-147">Yineleyici işlevi her çağrısı devam eder, sonraki yürütülmesi `Yield` sonraki yinelemesini sırasında oluşur deyimi `For…Next` döngü.</span><span class="sxs-lookup"><span data-stu-id="4a955-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="4a955-148">Yineleyici yöntemin dönüş türü <xref:System.Collections.Generic.IEnumerable%601>, bir yineleyici arabirimi türü.</span><span class="sxs-lookup"><span data-stu-id="4a955-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="4a955-149">Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="4a955-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="4a955-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a955-150">Example</span></span>  
 <span data-ttu-id="4a955-151">Aşağıdaki örnekte gösterilmiştir bir `Get` yineleyici olduğu erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="4a955-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="4a955-152">Özellik bildirimi içeren bir `Iterator` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="4a955-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 <span data-ttu-id="4a955-153">Ek örnekler için bkz: [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="4a955-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a955-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a955-154">See Also</span></span>  
 [<span data-ttu-id="4a955-155">Deyimler</span><span class="sxs-lookup"><span data-stu-id="4a955-155">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
