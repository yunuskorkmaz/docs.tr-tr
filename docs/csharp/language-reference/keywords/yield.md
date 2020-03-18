---
title: içeriksel anahtar kelime verim - C# Başvuru
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e3c9e37e7b543eaddae837a85604c4ba91fbc744
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712786"
---
# <a name="yield-c-reference"></a><span data-ttu-id="3ebaf-102">yield (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3ebaf-102">yield (C# Reference)</span></span>

<span data-ttu-id="3ebaf-103">Bir deyimde `yield` [bağlamsal anahtar kelimeyi](index.md#contextual-keywords) kullandığınızda, görüntülendiği yöntemin, işleç veya `get` erişimcinin bir yineleyici olduğunu belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-103">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="3ebaf-104">Bir `yield` yineleyici tanımlamak için kullanmak, özel bir koleksiyon türü için <xref:System.Collections.Generic.IEnumerator%601> <xref:System.Collections.IEnumerable> ve <xref:System.Collections.IEnumerator> deseni uyguladığınız zaman açık bir ek sınıf (numaralandırma için durumu tutan sınıf, örneğine bakın) gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="3ebaf-105">Aşağıdaki örnek, `yield` deyimin iki biçimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-105">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="3ebaf-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ebaf-106">Remarks</span></span>

<span data-ttu-id="3ebaf-107">Her öğeyi birer birer döndürmek için bir `yield return` deyim kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-107">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="3ebaf-108">Bir yineleyici yönteminden döndürülen [sıra, foreach](foreach-in.md) deyimi veya LINQ sorgusu kullanılarak tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-108">The sequence returned from an iterator method can be consumed by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="3ebaf-109">Döngünün `foreach` her yinelemesi yineleyici yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="3ebaf-110">Yineleyici `yield return` yönteminde bir deyime ulaşıldığında `expression` döndürülür ve koddaki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="3ebaf-111">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="3ebaf-112">Yinelemeyi sona `yield break` erdirmek için bir deyim kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-112">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="3ebaf-113">Yineleyiciler hakkında daha fazla bilgi için [bkz.](../../iterators.md)</span><span class="sxs-lookup"><span data-stu-id="3ebaf-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="3ebaf-114">Yineleyici yöntemleri ve erişime erişim</span><span class="sxs-lookup"><span data-stu-id="3ebaf-114">Iterator methods and get accessors</span></span>

<span data-ttu-id="3ebaf-115">Bir yineleyicinin bildirimi aşağıdaki gerekliliklerle uyuşmalıdır:</span><span class="sxs-lookup"><span data-stu-id="3ebaf-115">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="3ebaf-116">İade türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, <xref:System.Collections.Generic.IEnumerator%601>veya .</span><span class="sxs-lookup"><span data-stu-id="3ebaf-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="3ebaf-117">Beyannamede [hakem](ref.md) veya [çıkış](out-parameter-modifier.md) [parametreleri](in-parameter-modifier.md) olamaz.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-117">The declaration can't have any [in](in-parameter-modifier.md) [ref](ref.md) or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="3ebaf-118">Döndüren `yield` <xref:System.Collections.IEnumerable> veya <xref:System.Collections.IEnumerator> döndüren `object`bir yineleyici türü.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="3ebaf-119">Yineleyici dönerse <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.Generic.IEnumerator%601>deyimdeki `yield return` ifade türünden genel tür parametresine örtülü bir dönüştürme olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="3ebaf-120">Şuna bir `yield return` ekstre veya `yield break` deyim ekemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="3ebaf-120">You can't include a `yield return` or `yield break` statement in:</span></span>

- <span data-ttu-id="3ebaf-121">[Lambda ifadeler](../../programming-guide/statements-expressions-operators/lambda-expressions.md) ve [anonim yöntemler](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3ebaf-121">[Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) and [anonymous methods](../operators/delegate-operator.md).</span></span>

- <span data-ttu-id="3ebaf-122">Güvenli olmayan bloklar içeren yöntemler.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-122">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="3ebaf-123">Daha fazla bilgi için [güvenli olmayan.](unsafe.md)</span><span class="sxs-lookup"><span data-stu-id="3ebaf-123">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="3ebaf-124">Özel durum işleme</span><span class="sxs-lookup"><span data-stu-id="3ebaf-124">Exception handling</span></span>

<span data-ttu-id="3ebaf-125">Bir `yield return` deyim try-catch bloğunda bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-125">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="3ebaf-126">Bir `yield return` deyim, try-finally deyiminin try bloğunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-126">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="3ebaf-127">Bir `yield break` deyim bir try bloğunda veya yakalama bloğunda bulunabilir, ancak son bir blokta bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-127">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="3ebaf-128">`foreach` Gövde (yineleyici yöntemi nin dışında) bir özel durum `finally` atarsa, yineleyici yönteminde bir blok çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-128">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="3ebaf-129">Teknik uygulama</span><span class="sxs-lookup"><span data-stu-id="3ebaf-129">Technical implementation</span></span>

<span data-ttu-id="3ebaf-130">Aşağıdaki kod bir `IEnumerable<string>` yineleyici yönteminden bir döndürür ve sonra öğeleri ile yineleme.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-130">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="3ebaf-131">Çağrı, `MyIteratorMethod` yöntemin gövdesini yürütmez.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-131">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="3ebaf-132">Bunun yerine çağrı `IEnumerable<string>` `elements` değişkene bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-132">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="3ebaf-133">`foreach` Döngü bir yineleme üzerinde, <xref:System.Collections.IEnumerator.MoveNext%2A> yöntem için `elements`çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-133">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="3ebaf-134">Bu çağrı, bir `MyIteratorMethod` sonraki `yield return` ifadeye ulaşılına kadar gövdeyi yürütür.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-134">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="3ebaf-135">`yield return` İfade tarafından döndürülen ifade, yalnızca döngü `element` gövdesi tarafından tüketim için değişkenin <xref:System.Collections.Generic.IEnumerator%601.Current%2A> değerini `elements`değil, `IEnumerable<string>`aynı zamanda bir .</span><span class="sxs-lookup"><span data-stu-id="3ebaf-135">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="3ebaf-136">Döngünün `foreach` sonraki her yinelemesinde, yineleme gövdesinin yürütülmesi kaldığı yerden devam ediyor ve bir `yield return` ifadeye ulaştığında yine durur.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-136">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="3ebaf-137">Yineleme `foreach` yönteminin sonuna veya bir `yield break` ifadeye ulaşıldığında döngü tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-137">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="3ebaf-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ebaf-138">Example</span></span>

<span data-ttu-id="3ebaf-139">Aşağıdaki örnekte `yield return` bir `for` döngü içinde bir deyim vardır.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-139">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="3ebaf-140">Yöntemde ifade gövdesinin `foreach` `Main` her yineleme `Power` yineleyici işlevine bir çağrı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-140">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="3ebaf-141">Yineleyici işlevine yapılan her çağrı, `yield return` `for` döngünün bir sonraki yinelemesi sırasında oluşan deyimin bir sonraki yürütmesine ilerler.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-141">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="3ebaf-142">Yineleyici yönteminin dönüş <xref:System.Collections.IEnumerable>türü, bir yineleyici arabirim türüdür.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-142">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="3ebaf-143">Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-143">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="3ebaf-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ebaf-144">Example</span></span>

<span data-ttu-id="3ebaf-145">Aşağıdaki örnek, bir `get` yineleyici olan bir erişimci gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-145">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="3ebaf-146">Örnekte, her `yield return` deyim kullanıcı tanımlı bir sınıfın bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-146">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="3ebaf-147">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3ebaf-147">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3ebaf-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ebaf-148">See also</span></span>

- [<span data-ttu-id="3ebaf-149">C# Referans</span><span class="sxs-lookup"><span data-stu-id="3ebaf-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="3ebaf-150">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3ebaf-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3ebaf-151">foreach, in</span><span class="sxs-lookup"><span data-stu-id="3ebaf-151">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="3ebaf-152">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="3ebaf-152">Iterators</span></span>](../../iterators.md)
