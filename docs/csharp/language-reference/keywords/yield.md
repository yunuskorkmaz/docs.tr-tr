---
title: bağlamsal anahtar sözcük - yield C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: cfeef1d84a443163f4bbeda863682335d9cd1fcd
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222630"
---
# <a name="yield-c-reference"></a><span data-ttu-id="77b0a-102">yield (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="77b0a-102">yield (C# Reference)</span></span>

<span data-ttu-id="77b0a-103">Kullandığınızda `yield` [bağlamsal anahtar sözcük](index.md#contextual-keywords) bir deyimde, belirttiğiniz yöntemin, işlecin veya `get` erişimci görünür olan bir yineleyici.</span><span class="sxs-lookup"><span data-stu-id="77b0a-103">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="77b0a-104">Kullanarak `yield` bir yineleyici tanımlamak için açık bir ekstra sınıf gereksinimini ortadan kaldırır (bir numaralandırma için durumu tutan sınıf, bkz <xref:System.Collections.Generic.IEnumerator%601> örneği) uyguladığınızda <xref:System.Collections.IEnumerable> ve <xref:System.Collections.IEnumerator> özel bir koleksiyona deseni yazın.</span><span class="sxs-lookup"><span data-stu-id="77b0a-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="77b0a-105">Aşağıdaki örnek, iki formunu gösterir `yield` deyimi.</span><span class="sxs-lookup"><span data-stu-id="77b0a-105">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="77b0a-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77b0a-106">Remarks</span></span>

<span data-ttu-id="77b0a-107">Kullandığınız bir `yield return` her öğeyi bir defada döndürmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="77b0a-107">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="77b0a-108">Kullanarak bir yineleyici yöntemini kullanan bir [foreach](foreach-in.md) deyimini veya LINQ sorgusunu.</span><span class="sxs-lookup"><span data-stu-id="77b0a-108">You consume an iterator method by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="77b0a-109">Her bir yinelemesini `foreach` döngüsü yineleyici yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="77b0a-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="77b0a-110">Olduğunda bir `yield return` yineleyici yöntem içinde deyimine ulaşıldığında `expression` döndürülür ve kodun geçerli konumu korunur.</span><span class="sxs-lookup"><span data-stu-id="77b0a-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="77b0a-111">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="77b0a-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="77b0a-112">Kullanabileceğiniz bir `yield break` yinelemeyi sonlandırmak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="77b0a-112">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="77b0a-113">Yineleyiciler hakkında daha fazla bilgi için bkz: [yineleyiciler](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="77b0a-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="77b0a-114">Yineleyici yöntemleri ve get erişimcileri</span><span class="sxs-lookup"><span data-stu-id="77b0a-114">Iterator methods and get accessors</span></span>

<span data-ttu-id="77b0a-115">Bir yineleyicinin bildirimi aşağıdaki gerekliliklerle uyuşmalıdır:</span><span class="sxs-lookup"><span data-stu-id="77b0a-115">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="77b0a-116">Dönüş türü olmalıdır <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="77b0a-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="77b0a-117">Bildirimi içeremez [içinde](in-parameter-modifier.md) [ref](ref.md) veya [kullanıma](out-parameter-modifier.md) parametreleri.</span><span class="sxs-lookup"><span data-stu-id="77b0a-117">The declaration can't have any [in](in-parameter-modifier.md) [ref](ref.md) or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="77b0a-118">`yield` Türü döndüren bir yineleyicinin <xref:System.Collections.IEnumerable> veya <xref:System.Collections.IEnumerator> olduğu `object`.</span><span class="sxs-lookup"><span data-stu-id="77b0a-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="77b0a-119">Yineleyici döndürürse <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.Generic.IEnumerator%601>, ifadesinde türü örtük bir dönüştürme olmalıdır `yield return` genel tür parametresine deyimi.</span><span class="sxs-lookup"><span data-stu-id="77b0a-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="77b0a-120">Dahil edemezsiniz bir `yield return` veya `yield break` aşağıdaki özelliklere sahip yöntemlerini deyiminin:</span><span class="sxs-lookup"><span data-stu-id="77b0a-120">You can't include a `yield return` or `yield break` statement in methods that have the following characteristics:</span></span>

- <span data-ttu-id="77b0a-121">Anonim yöntemler.</span><span class="sxs-lookup"><span data-stu-id="77b0a-121">Anonymous methods.</span></span> <span data-ttu-id="77b0a-122">Daha fazla bilgi için [anonim yöntemler](../../programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="77b0a-122">For more information, see [Anonymous Methods](../../programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>

- <span data-ttu-id="77b0a-123">Güvenli olmayan bloklar içeren yöntemler.</span><span class="sxs-lookup"><span data-stu-id="77b0a-123">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="77b0a-124">Daha fazla bilgi için [güvenli](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="77b0a-124">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="77b0a-125">Özel durum işleme</span><span class="sxs-lookup"><span data-stu-id="77b0a-125">Exception handling</span></span>

<span data-ttu-id="77b0a-126">A `yield return` ifadesi bir try-catch bloğu içinde bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="77b0a-126">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="77b0a-127">A `yield return` ifadesi bir try-finally ifadesinin try bloğunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="77b0a-127">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="77b0a-128">A `yield break` ifadesi bir try bloğu ya da bir catch bloğu içinde bulunabilir ama bir finally bloğunda.</span><span class="sxs-lookup"><span data-stu-id="77b0a-128">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="77b0a-129">Varsa `foreach` gövdesi (yineleyici yöntemi dışında) bir özel durum oluşturursa bir `finally` yineleyici yöntem bloğunda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="77b0a-129">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="77b0a-130">Teknik uygulama</span><span class="sxs-lookup"><span data-stu-id="77b0a-130">Technical implementation</span></span>

<span data-ttu-id="77b0a-131">Aşağıdaki kod döndürür bir `IEnumerable<string>` yineleyici yöntemden ve sonra öğeleri boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="77b0a-131">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="77b0a-132">Çağrı `MyIteratorMethod` yöntemin gövdesini yürütmez.</span><span class="sxs-lookup"><span data-stu-id="77b0a-132">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="77b0a-133">Bunun yerine çağrı döndürür bir `IEnumerable<string>` içine `elements` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="77b0a-133">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="77b0a-134">Yinelemesi üzerinde `foreach` döngü <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için çağrılır `elements`.</span><span class="sxs-lookup"><span data-stu-id="77b0a-134">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="77b0a-135">Bu çağrı gövdesini yürütür `MyIteratorMethod` sonraki kadar `yield return` deyimine ulaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="77b0a-135">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="77b0a-136">Tarafından döndürülen ifade `yield return` deyimi yalnızca değerini belirler `element` döngü gövdesinin tüketimi için değişken aynı zamanda <xref:System.Collections.Generic.IEnumerator%601.Current%2A> özelliği `elements`, olduğu bir `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="77b0a-136">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="77b0a-137">Her yinelemesinde `foreach` kadar yineleyici gövdenin yürütülmesi devam eder, döngü onu ulaştığında yeniden kaldığı bir `yield return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="77b0a-137">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="77b0a-138">`foreach` Tamamlandıktan döngüsü yineleyici yöntemin sonuna ya da bir `yield break` deyimine ulaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="77b0a-138">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="77b0a-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="77b0a-139">Example</span></span>

<span data-ttu-id="77b0a-140">Aşağıdaki örnek sahip bir `yield return` içindeki bir `for` döngü.</span><span class="sxs-lookup"><span data-stu-id="77b0a-140">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="77b0a-141">Her bir yinelemesini `foreach` deyiminin gövdesinde `Main` yöntemine bir çağrı oluşturur `Power` yineleyici işlevi.</span><span class="sxs-lookup"><span data-stu-id="77b0a-141">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="77b0a-142">Her yineleyici işleve çağrı için sonraki yürütme devam eder `yield return` sıradaki yinelemesi süresince gerçekleşen deyimi `for` döngü.</span><span class="sxs-lookup"><span data-stu-id="77b0a-142">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="77b0a-143">Yineleyici yöntemin dönüş türü <xref:System.Collections.IEnumerable>, bir yineleyici arabirimi türü.</span><span class="sxs-lookup"><span data-stu-id="77b0a-143">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="77b0a-144">Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="77b0a-144">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="77b0a-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="77b0a-145">Example</span></span>

<span data-ttu-id="77b0a-146">Aşağıdaki örnek, gösterir bir `get` bir yineleyici erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="77b0a-146">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="77b0a-147">Örnekte, her `yield return` deyimi, kullanıcı tanımlı bir sınıfın bir örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="77b0a-147">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="77b0a-148">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="77b0a-148">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="77b0a-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77b0a-149">See also</span></span>

- [<span data-ttu-id="77b0a-150">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="77b0a-150">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="77b0a-151">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="77b0a-151">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="77b0a-152">foreach, in</span><span class="sxs-lookup"><span data-stu-id="77b0a-152">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="77b0a-153">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="77b0a-153">Iterators</span></span>](../../iterators.md)