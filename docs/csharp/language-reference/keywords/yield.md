---
description: yield bağlamsal anahtar sözcüğü-C# başvurusu
title: yield bağlamsal anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: c8caf7e34397faf9f7085d6634287cffcb37eb08
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141887"
---
# <a name="yield-c-reference"></a><span data-ttu-id="35a3c-103">yield (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="35a3c-103">yield (C# Reference)</span></span>

<span data-ttu-id="35a3c-104">`yield`Bir ifadede [bağlamsal anahtar sözcüğünü](index.md#contextual-keywords) kullandığınızda, görünen yöntemin, işlecin veya `get` erişimcinin bir yineleyici olduğunu belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35a3c-104">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="35a3c-105">Bir `yield` Yineleyici tanımlamak için kullanmak, <xref:System.Collections.Generic.IEnumerator%601> <xref:System.Collections.IEnumerable> özel bir koleksiyon türü için ve modelini uyguladığınızda açık bir ek sınıfa (bir sabit listesinin durumunu tutan sınıf için bkz. bir örnek için bkz.) gereksinimi ortadan kaldırır <xref:System.Collections.IEnumerator> .</span><span class="sxs-lookup"><span data-stu-id="35a3c-105">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="35a3c-106">Aşağıdaki örnekte, ifadesinin iki formu gösterilmektedir `yield` .</span><span class="sxs-lookup"><span data-stu-id="35a3c-106">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="35a3c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35a3c-107">Remarks</span></span>

<span data-ttu-id="35a3c-108">`yield return`Her öğeyi birer birer döndürmek için bir ifade kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="35a3c-108">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="35a3c-109">Bir yineleyici yönteminden döndürülen sıra, [foreach](foreach-in.md) IFADESI veya LINQ sorgusu kullanılarak tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="35a3c-109">The sequence returned from an iterator method can be consumed by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="35a3c-110">Döngünün her yinelemesi `foreach` yineleyici yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="35a3c-110">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="35a3c-111">`yield return`Yineleyici yönteminde bir ifadeye ulaşıldığında, `expression` döndürülür ve koddaki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="35a3c-111">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="35a3c-112">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="35a3c-112">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="35a3c-113">`yield break`Yinelemeyi sonlandırmak için bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35a3c-113">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="35a3c-114">Yineleyiciler hakkında daha fazla bilgi için bkz. [yineleyiciler](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="35a3c-114">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="35a3c-115">Yineleyici yöntemleri ve get erişimcileri</span><span class="sxs-lookup"><span data-stu-id="35a3c-115">Iterator methods and get accessors</span></span>

<span data-ttu-id="35a3c-116">Bir yineleyicinin bildirimi aşağıdaki gerekliliklerle uyuşmalıdır:</span><span class="sxs-lookup"><span data-stu-id="35a3c-116">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="35a3c-117">Dönüş türü <xref:System.Collections.IEnumerable> ,, veya olmalıdır <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="35a3c-117">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="35a3c-118">Bildirimin [in](in-parameter-modifier.md) [ref](ref.md) veya [Out](out-parameter-modifier.md) parametreleri olamaz.</span><span class="sxs-lookup"><span data-stu-id="35a3c-118">The declaration can't have any [in](in-parameter-modifier.md) [ref](ref.md) or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="35a3c-119">`yield`Veya döndüren bir yineleyici türü <xref:System.Collections.IEnumerable> <xref:System.Collections.IEnumerator> `object` .</span><span class="sxs-lookup"><span data-stu-id="35a3c-119">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="35a3c-120">Yineleyici <xref:System.Collections.Generic.IEnumerable%601> veya döndürürse, deyimde <xref:System.Collections.Generic.IEnumerator%601> deyim türünden genel tür parametresine örtük bir dönüştürme olmalıdır `yield return` .</span><span class="sxs-lookup"><span data-stu-id="35a3c-120">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="35a3c-121">`yield return` `yield break` İçine or ifadesini ekleyemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="35a3c-121">You can't include a `yield return` or `yield break` statement in:</span></span>

- <span data-ttu-id="35a3c-122">[Lambda ifadeleri](../operators/lambda-expressions.md) ve [Anonim yöntemler](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="35a3c-122">[Lambda expressions](../operators/lambda-expressions.md) and [anonymous methods](../operators/delegate-operator.md).</span></span>

- <span data-ttu-id="35a3c-123">Güvenli olmayan bloklar içeren yöntemler.</span><span class="sxs-lookup"><span data-stu-id="35a3c-123">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="35a3c-124">Daha fazla bilgi için bkz. [güvenli değil](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="35a3c-124">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="35a3c-125">Özel durum işleme</span><span class="sxs-lookup"><span data-stu-id="35a3c-125">Exception handling</span></span>

<span data-ttu-id="35a3c-126">Bir `yield return` ifade, try-catch bloğunda bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="35a3c-126">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="35a3c-127">Bir `yield return` ifade, try-finally ifadesinin try bloğunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="35a3c-127">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="35a3c-128">Bir `yield break` ifade bir try bloğunda veya catch bloğunda bulunabilir, ancak finally bloğunda yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="35a3c-128">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="35a3c-129">`foreach`Gövde (yineleyici yönteminin dışında) bir özel durum oluşturursa, `finally` yineleyici yönteminde bir blok yürütülür.</span><span class="sxs-lookup"><span data-stu-id="35a3c-129">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="35a3c-130">Teknik uygulama</span><span class="sxs-lookup"><span data-stu-id="35a3c-130">Technical implementation</span></span>

<span data-ttu-id="35a3c-131">Aşağıdaki kod bir `IEnumerable<string>` Yineleyici yönteminden bir döndürür ve sonra öğeleri boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="35a3c-131">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="35a3c-132">Çağrısı, `MyIteratorMethod` yönteminin gövdesini yürütmez.</span><span class="sxs-lookup"><span data-stu-id="35a3c-132">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="35a3c-133">Bunun yerine, çağrı `IEnumerable<string>` değişkenine bir döndürür `elements` .</span><span class="sxs-lookup"><span data-stu-id="35a3c-133">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="35a3c-134">Döngüsünün bir yinelemesinde `foreach` , <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için çağrılır `elements` .</span><span class="sxs-lookup"><span data-stu-id="35a3c-134">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="35a3c-135">Bu çağrı, `MyIteratorMethod` sonraki `yield return` ifadeye ulaşılana kadar gövdesini yürütür.</span><span class="sxs-lookup"><span data-stu-id="35a3c-135">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="35a3c-136">Deyimi tarafından döndürülen ifade, `yield return` yalnızca `element` döngü gövdesi tarafından tüketim için değişkenin değerini değil <xref:System.Collections.Generic.IEnumerator%601.Current%2A> , öğesinin özelliğini de bir olarak belirler `elements` `IEnumerable<string>` .</span><span class="sxs-lookup"><span data-stu-id="35a3c-136">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="35a3c-137">Döngünün sonraki tekrarında `foreach` , yineleyici gövdesinin yürütülmesi kaldığınız yerden devam eder, bir ifadeye ulaştığında yeniden durdurulur `yield return` .</span><span class="sxs-lookup"><span data-stu-id="35a3c-137">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="35a3c-138">`foreach`Yineleyici yönteminin sonuna veya bir `yield break` ifadeye ulaşıldığında döngü tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="35a3c-138">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="35a3c-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="35a3c-139">Example</span></span>

<span data-ttu-id="35a3c-140">Aşağıdaki örnekte, `yield return` döngüsünün içinde olan bir ifade vardır `for` .</span><span class="sxs-lookup"><span data-stu-id="35a3c-140">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="35a3c-141">`foreach`Yöntemi içindeki ifade gövdesinin her yinelemesi, `Main` Yineleyici işlevine bir çağrı oluşturur `Power` .</span><span class="sxs-lookup"><span data-stu-id="35a3c-141">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="35a3c-142">Yineleyici işlevine yapılan her çağrı, `yield return` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan deyimin bir sonraki yürütmeye ilerler `for` .</span><span class="sxs-lookup"><span data-stu-id="35a3c-142">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="35a3c-143">Yineleyici yönteminin dönüş türü <xref:System.Collections.IEnumerable> , yineleyici arabirim türü olan.</span><span class="sxs-lookup"><span data-stu-id="35a3c-143">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="35a3c-144">Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="35a3c-144">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="35a3c-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="35a3c-145">Example</span></span>

<span data-ttu-id="35a3c-146">Aşağıdaki örnek, `get` Yineleyici olan bir erişimciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="35a3c-146">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="35a3c-147">Örnekte, her bir `yield return` ifade Kullanıcı tanımlı bir sınıfın bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="35a3c-147">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="35a3c-148">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="35a3c-148">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="35a3c-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35a3c-149">See also</span></span>

- [<span data-ttu-id="35a3c-150">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="35a3c-150">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="35a3c-151">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="35a3c-151">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="35a3c-152">foreach, in</span><span class="sxs-lookup"><span data-stu-id="35a3c-152">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="35a3c-153">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="35a3c-153">Iterators</span></span>](../../iterators.md)
