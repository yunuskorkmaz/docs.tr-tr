---
title: yield bağlamsal anahtar sözcük C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e3c9e37e7b543eaddae837a85604c4ba91fbc744
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712786"
---
# <a name="yield-c-reference"></a><span data-ttu-id="60ac1-102">yield (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="60ac1-102">yield (C# Reference)</span></span>

<span data-ttu-id="60ac1-103">Bir ifadede `yield` [bağlamsal anahtar sözcüğünü](index.md#contextual-keywords) kullandığınızda, göründüğü yöntemin, işlecin veya `get` erişimcisinin bir yineleyici olduğunu belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60ac1-103">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="60ac1-104">Bir yineleyici tanımlamak için `yield` kullanmak, özel bir koleksiyon türü için <xref:System.Collections.IEnumerable> ve <xref:System.Collections.IEnumerator> modelini uyguladığınızda, açık bir ek sınıfa yönelik gereksinimi ortadan kaldırır (bir numaralandırma için durumu tutan sınıf, bir örnek için bkz. <xref:System.Collections.Generic.IEnumerator%601>).</span><span class="sxs-lookup"><span data-stu-id="60ac1-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="60ac1-105">Aşağıdaki örnek `yield` deyimin iki biçimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="60ac1-105">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="60ac1-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60ac1-106">Remarks</span></span>

<span data-ttu-id="60ac1-107">Her bir öğeyi birer birer döndürmek için bir `yield return` ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="60ac1-107">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="60ac1-108">Bir yineleyici yönteminden döndürülen sıra, [foreach](foreach-in.md) IFADESI veya LINQ sorgusu kullanılarak tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="60ac1-108">The sequence returned from an iterator method can be consumed by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="60ac1-109">`foreach` döngüsünün her yinelemesi yineleyici yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="60ac1-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="60ac1-110">Yineleyici yönteminde bir `yield return` ifadesine ulaşıldığında, `expression` döndürülür ve koddaki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="60ac1-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="60ac1-111">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="60ac1-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="60ac1-112">Yinelemeyi sonlandırmak için `yield break` bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60ac1-112">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="60ac1-113">Yineleyiciler hakkında daha fazla bilgi için bkz. [yineleyiciler](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="60ac1-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="60ac1-114">Yineleyici yöntemleri ve get erişimcileri</span><span class="sxs-lookup"><span data-stu-id="60ac1-114">Iterator methods and get accessors</span></span>

<span data-ttu-id="60ac1-115">Bir yineleyicinin bildirimi aşağıdaki gerekliliklerle uyuşmalıdır:</span><span class="sxs-lookup"><span data-stu-id="60ac1-115">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="60ac1-116">Dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>veya <xref:System.Collections.Generic.IEnumerator%601>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60ac1-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="60ac1-117">Bildirimin [parametreleri olamaz](in-parameter-modifier.md) [ref](ref.md) veya [Out](out-parameter-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="60ac1-117">The declaration can't have any [in](in-parameter-modifier.md) [ref](ref.md) or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="60ac1-118"><xref:System.Collections.IEnumerable> veya <xref:System.Collections.IEnumerator> döndüren bir yineleyicinin `yield` türü `object`.</span><span class="sxs-lookup"><span data-stu-id="60ac1-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="60ac1-119">Yineleyici <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.Generic.IEnumerator%601>döndürürse, `yield return` deyimindeki ifadenin türünden genel tür parametresine örtük bir dönüştürme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60ac1-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="60ac1-120">İçine bir `yield return` veya `yield break` ifadesini ekleyemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="60ac1-120">You can't include a `yield return` or `yield break` statement in:</span></span>

- <span data-ttu-id="60ac1-121">[Lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md) ve [Anonim yöntemler](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="60ac1-121">[Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) and [anonymous methods](../operators/delegate-operator.md).</span></span>

- <span data-ttu-id="60ac1-122">Güvenli olmayan bloklar içeren yöntemler.</span><span class="sxs-lookup"><span data-stu-id="60ac1-122">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="60ac1-123">Daha fazla bilgi için bkz. [güvenli değil](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="60ac1-123">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="60ac1-124">Özel durum işleme</span><span class="sxs-lookup"><span data-stu-id="60ac1-124">Exception handling</span></span>

<span data-ttu-id="60ac1-125">Bir `yield return` deyimleri, try-catch bloğunda bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="60ac1-125">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="60ac1-126">Bir `yield return` deyimleri, try-finally ifadesinin try bloğunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="60ac1-126">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="60ac1-127">`yield break` bir ifade, bir try bloğunda veya catch bloğunda bulunabilir ancak finally bloğunda yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="60ac1-127">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="60ac1-128">`foreach` gövdesi (yineleyici yöntemi dışında) bir özel durum oluşturursa, yineleyici yönteminde bir `finally` bloğu yürütülür.</span><span class="sxs-lookup"><span data-stu-id="60ac1-128">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="60ac1-129">Teknik uygulama</span><span class="sxs-lookup"><span data-stu-id="60ac1-129">Technical implementation</span></span>

<span data-ttu-id="60ac1-130">Aşağıdaki kod bir yineleyici yönteminden bir `IEnumerable<string>` döndürür ve sonra öğeleri boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="60ac1-130">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="60ac1-131">`MyIteratorMethod` çağrısı, yönteminin gövdesini yürütmez.</span><span class="sxs-lookup"><span data-stu-id="60ac1-131">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="60ac1-132">Bunun yerine, çağrı `elements` değişkenine bir `IEnumerable<string>` döndürür.</span><span class="sxs-lookup"><span data-stu-id="60ac1-132">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="60ac1-133">`foreach` döngüsünün bir yinelemesi üzerinde `elements`için <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="60ac1-133">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="60ac1-134">Bu çağrı, sonraki `yield return` ifadesine ulaşılana kadar `MyIteratorMethod` gövdesini yürütür.</span><span class="sxs-lookup"><span data-stu-id="60ac1-134">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="60ac1-135">`yield return` deyiminin döndürdüğü ifade, yalnızca döngü gövdesine göre tüketim için `element` değişkeninin değerini değil, bir `IEnumerable<string>`olan `elements`<xref:System.Collections.Generic.IEnumerator%601.Current%2A> özelliğini de belirler.</span><span class="sxs-lookup"><span data-stu-id="60ac1-135">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="60ac1-136">`foreach` döngüsünün sonraki tekrarında, yineleyici gövdesinin yürütülmesi kaldığınız yerden devam eder, bir `yield return` bildirimine ulaştığında yeniden durdurulur.</span><span class="sxs-lookup"><span data-stu-id="60ac1-136">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="60ac1-137">Yineleyici yönteminin sonuna veya bir `yield break` ifadesine ulaşıldığında `foreach` döngüsü tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="60ac1-137">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="60ac1-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="60ac1-138">Example</span></span>

<span data-ttu-id="60ac1-139">Aşağıdaki örnek, bir `for` döngüsünün içindeki bir `yield return` bildirimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="60ac1-139">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="60ac1-140">`Main` yönteminde `foreach` bildiri gövdesinin her yinelemesi `Power` Yineleyici işlevine bir çağrı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="60ac1-140">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="60ac1-141">Yineleyici işlevine yapılan her çağrı, `for` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan `yield return` deyimin bir sonraki yürütmeye ilerler.</span><span class="sxs-lookup"><span data-stu-id="60ac1-141">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="60ac1-142">Yineleyici yönteminin dönüş türü, bir Yineleyici arabirimi türü olan <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="60ac1-142">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="60ac1-143">Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="60ac1-143">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="60ac1-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="60ac1-144">Example</span></span>

<span data-ttu-id="60ac1-145">Aşağıdaki örnek, yineleyici olan bir `get` erişimcisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="60ac1-145">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="60ac1-146">Örnekte, her `yield return` ekstresi Kullanıcı tanımlı bir sınıfın bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="60ac1-146">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="60ac1-147">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="60ac1-147">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="60ac1-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60ac1-148">See also</span></span>

- [<span data-ttu-id="60ac1-149">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="60ac1-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="60ac1-150">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="60ac1-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="60ac1-151">foreach, in</span><span class="sxs-lookup"><span data-stu-id="60ac1-151">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="60ac1-152">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="60ac1-152">Iterators</span></span>](../../iterators.md)
