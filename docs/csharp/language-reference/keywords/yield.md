---
title: yield bağlamsal anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: d3fe4cf92ca17457bd541f092f5d146ba6c1c095
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794422"
---
# <a name="yield-c-reference"></a><span data-ttu-id="b0272-102">yield (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b0272-102">yield (C# Reference)</span></span>

<span data-ttu-id="b0272-103">`yield`Bir ifadede [bağlamsal anahtar sözcüğünü](index.md#contextual-keywords) kullandığınızda, görünen yöntemin, işlecin veya `get` erişimcinin bir yineleyici olduğunu belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0272-103">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="b0272-104">Bir `yield` Yineleyici tanımlamak için kullanmak, <xref:System.Collections.Generic.IEnumerator%601> <xref:System.Collections.IEnumerable> özel bir koleksiyon türü için ve modelini uyguladığınızda açık bir ek sınıfa (bir sabit listesinin durumunu tutan sınıf için bkz. bir örnek için bkz.) gereksinimi ortadan kaldırır <xref:System.Collections.IEnumerator> .</span><span class="sxs-lookup"><span data-stu-id="b0272-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="b0272-105">Aşağıdaki örnekte, ifadesinin iki formu gösterilmektedir `yield` .</span><span class="sxs-lookup"><span data-stu-id="b0272-105">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="b0272-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0272-106">Remarks</span></span>

<span data-ttu-id="b0272-107">`yield return`Her öğeyi birer birer döndürmek için bir ifade kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b0272-107">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="b0272-108">Bir yineleyici yönteminden döndürülen sıra, [foreach](foreach-in.md) IFADESI veya LINQ sorgusu kullanılarak tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="b0272-108">The sequence returned from an iterator method can be consumed by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="b0272-109">Döngünün her yinelemesi `foreach` yineleyici yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="b0272-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="b0272-110">`yield return`Yineleyici yönteminde bir ifadeye ulaşıldığında, `expression` döndürülür ve koddaki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="b0272-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="b0272-111">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="b0272-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="b0272-112">`yield break`Yinelemeyi sonlandırmak için bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0272-112">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="b0272-113">Yineleyiciler hakkında daha fazla bilgi için bkz. [yineleyiciler](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="b0272-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="b0272-114">Yineleyici yöntemleri ve get erişimcileri</span><span class="sxs-lookup"><span data-stu-id="b0272-114">Iterator methods and get accessors</span></span>

<span data-ttu-id="b0272-115">Bir yineleyicinin bildirimi aşağıdaki gerekliliklerle uyuşmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b0272-115">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="b0272-116">Dönüş türü <xref:System.Collections.IEnumerable> ,, veya olmalıdır <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="b0272-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="b0272-117">Bildirimin [in](in-parameter-modifier.md) [ref](ref.md) veya [Out](out-parameter-modifier.md) parametreleri olamaz.</span><span class="sxs-lookup"><span data-stu-id="b0272-117">The declaration can't have any [in](in-parameter-modifier.md) [ref](ref.md) or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="b0272-118">`yield`Veya döndüren bir yineleyici türü <xref:System.Collections.IEnumerable> <xref:System.Collections.IEnumerator> `object` .</span><span class="sxs-lookup"><span data-stu-id="b0272-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="b0272-119">Yineleyici <xref:System.Collections.Generic.IEnumerable%601> veya döndürürse, deyimde <xref:System.Collections.Generic.IEnumerator%601> deyim türünden genel tür parametresine örtük bir dönüştürme olmalıdır `yield return` .</span><span class="sxs-lookup"><span data-stu-id="b0272-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="b0272-120">`yield return` `yield break` İçine or ifadesini ekleyemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="b0272-120">You can't include a `yield return` or `yield break` statement in:</span></span>

- <span data-ttu-id="b0272-121">[Lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md) ve [Anonim yöntemler](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b0272-121">[Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) and [anonymous methods](../operators/delegate-operator.md).</span></span>

- <span data-ttu-id="b0272-122">Güvenli olmayan bloklar içeren yöntemler.</span><span class="sxs-lookup"><span data-stu-id="b0272-122">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="b0272-123">Daha fazla bilgi için bkz. [güvenli değil](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="b0272-123">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="b0272-124">Özel durum işleme</span><span class="sxs-lookup"><span data-stu-id="b0272-124">Exception handling</span></span>

<span data-ttu-id="b0272-125">Bir `yield return` ifade, try-catch bloğunda bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="b0272-125">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="b0272-126">Bir `yield return` ifade, try-finally ifadesinin try bloğunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b0272-126">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="b0272-127">Bir `yield break` ifade bir try bloğunda veya catch bloğunda bulunabilir, ancak finally bloğunda yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="b0272-127">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="b0272-128">`foreach`Gövde (yineleyici yönteminin dışında) bir özel durum oluşturursa, `finally` yineleyici yönteminde bir blok yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b0272-128">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="b0272-129">Teknik uygulama</span><span class="sxs-lookup"><span data-stu-id="b0272-129">Technical implementation</span></span>

<span data-ttu-id="b0272-130">Aşağıdaki kod bir `IEnumerable<string>` Yineleyici yönteminden bir döndürür ve sonra öğeleri boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="b0272-130">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="b0272-131">Çağrısı, `MyIteratorMethod` yönteminin gövdesini yürütmez.</span><span class="sxs-lookup"><span data-stu-id="b0272-131">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="b0272-132">Bunun yerine, çağrı `IEnumerable<string>` değişkenine bir döndürür `elements` .</span><span class="sxs-lookup"><span data-stu-id="b0272-132">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="b0272-133">Döngüsünün bir yinelemesinde `foreach` , <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için çağrılır `elements` .</span><span class="sxs-lookup"><span data-stu-id="b0272-133">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="b0272-134">Bu çağrı, `MyIteratorMethod` sonraki `yield return` ifadeye ulaşılana kadar gövdesini yürütür.</span><span class="sxs-lookup"><span data-stu-id="b0272-134">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="b0272-135">Deyimi tarafından döndürülen ifade, `yield return` yalnızca `element` döngü gövdesi tarafından tüketim için değişkenin değerini değil <xref:System.Collections.Generic.IEnumerator%601.Current%2A> , öğesinin özelliğini de bir olarak belirler `elements` `IEnumerable<string>` .</span><span class="sxs-lookup"><span data-stu-id="b0272-135">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="b0272-136">Döngünün sonraki tekrarında `foreach` , yineleyici gövdesinin yürütülmesi kaldığınız yerden devam eder, bir ifadeye ulaştığında yeniden durdurulur `yield return` .</span><span class="sxs-lookup"><span data-stu-id="b0272-136">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="b0272-137">`foreach`Yineleyici yönteminin sonuna veya bir `yield break` ifadeye ulaşıldığında döngü tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="b0272-137">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="b0272-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0272-138">Example</span></span>

<span data-ttu-id="b0272-139">Aşağıdaki örnekte, `yield return` döngüsünün içinde olan bir ifade vardır `for` .</span><span class="sxs-lookup"><span data-stu-id="b0272-139">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="b0272-140">`foreach`Yöntemi içindeki ifade gövdesinin her yinelemesi, `Main` Yineleyici işlevine bir çağrı oluşturur `Power` .</span><span class="sxs-lookup"><span data-stu-id="b0272-140">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="b0272-141">Yineleyici işlevine yapılan her çağrı, `yield return` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan deyimin bir sonraki yürütmeye ilerler `for` .</span><span class="sxs-lookup"><span data-stu-id="b0272-141">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="b0272-142">Yineleyici yönteminin dönüş türü <xref:System.Collections.IEnumerable> , yineleyici arabirim türü olan.</span><span class="sxs-lookup"><span data-stu-id="b0272-142">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="b0272-143">Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="b0272-143">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="b0272-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0272-144">Example</span></span>

<span data-ttu-id="b0272-145">Aşağıdaki örnek, `get` Yineleyici olan bir erişimciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0272-145">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="b0272-146">Örnekte, her bir `yield return` ifade Kullanıcı tanımlı bir sınıfın bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b0272-146">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="b0272-147">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b0272-147">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b0272-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0272-148">See also</span></span>

- [<span data-ttu-id="b0272-149">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b0272-149">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b0272-150">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b0272-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b0272-151">foreach, in</span><span class="sxs-lookup"><span data-stu-id="b0272-151">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="b0272-152">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="b0272-152">Iterators</span></span>](../../iterators.md)
