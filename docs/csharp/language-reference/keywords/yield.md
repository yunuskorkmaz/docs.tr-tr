---
title: yield (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: b22822656860b58a2f225fadcb3c68802899a505
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289431"
---
# <a name="yield-c-reference"></a><span data-ttu-id="f00d0-102">yield (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f00d0-102">yield (C# Reference)</span></span>
<span data-ttu-id="f00d0-103">Kullandığınızda `yield` anahtar sözcüğü bir deyimde size bildiren işleci, yöntemi veya `get` görünür olan yineleyici erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="f00d0-103">When you use the `yield` keyword in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="f00d0-104">Kullanarak `yield` yineleyici tanımlamak için bir açık ek sınıf gereksinimini ortadan kaldırır (bkz: bir numaralandırma durumu tutan sınıfı <xref:System.Collections.Generic.IEnumerator%601> bir örnek) ne zaman uygulamak <xref:System.Collections.IEnumerable> ve <xref:System.Collections.IEnumerator> özel bir koleksiyon için deseni yazın.</span><span class="sxs-lookup"><span data-stu-id="f00d0-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>  
  
 <span data-ttu-id="f00d0-105">Aşağıdaki örnek, iki tür gösterir `yield` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f00d0-105">The following example shows the two forms of the `yield` statement.</span></span>  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a><span data-ttu-id="f00d0-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f00d0-106">Remarks</span></span>  
 <span data-ttu-id="f00d0-107">Kullandığınız bir `yield return` her öğeye aynı anda geri dönmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="f00d0-107">You use a `yield return` statement to return each element one at a time.</span></span>  
  
 <span data-ttu-id="f00d0-108">İterator yöntemi ile kullanmasını bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi veya LINQ sorgusu.</span><span class="sxs-lookup"><span data-stu-id="f00d0-108">You consume an iterator method by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="f00d0-109">Her yinelemesinden `foreach` döngü yineleyici yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="f00d0-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="f00d0-110">Zaman bir `yield return` deyimi yineleyici yönteminde ulaşıldığında `expression` döndürülür ve kod geçerli konumda korunur.</span><span class="sxs-lookup"><span data-stu-id="f00d0-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="f00d0-111">Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.</span><span class="sxs-lookup"><span data-stu-id="f00d0-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="f00d0-112">Kullanabileceğiniz bir `yield break` yinelemeyi sonlandırmak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="f00d0-112">You can use a `yield break` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="f00d0-113">Yineleyiciler hakkında daha fazla bilgi için bkz: [yineleyiciler](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="f00d0-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>  
  
## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="f00d0-114">Yineleyici Yöntemleri ve get Erişimcileri</span><span class="sxs-lookup"><span data-stu-id="f00d0-114">Iterator Methods and get Accessors</span></span>  
 <span data-ttu-id="f00d0-115">Bir yineleyicinin bildirimi aşağıdaki gerekliliklerle uyuşmalıdır:</span><span class="sxs-lookup"><span data-stu-id="f00d0-115">The declaration of an iterator must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="f00d0-116">Dönüş türü olmalıdır <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="f00d0-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="f00d0-117">Bildirimi içeremez [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri.</span><span class="sxs-lookup"><span data-stu-id="f00d0-117">The declaration can't have any [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>  
  
 <span data-ttu-id="f00d0-118">`yield` Döndürür yineleyici türünü <xref:System.Collections.IEnumerable> veya <xref:System.Collections.IEnumerator> olan `object`.</span><span class="sxs-lookup"><span data-stu-id="f00d0-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="f00d0-119">Yineleyici döndürürse <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.Generic.IEnumerator%601>, ifadesinde türü örtük bir dönüştürme olmalıdır `yield return` genel tür parametresi ifadesine.</span><span class="sxs-lookup"><span data-stu-id="f00d0-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>  
  
 <span data-ttu-id="f00d0-120">Dahil edilemiyor bir `yield return` veya `yield break` aşağıdaki özelliklere sahip yöntemleri deyiminde:</span><span class="sxs-lookup"><span data-stu-id="f00d0-120">You can't include a `yield return` or `yield break` statement in methods that have the following characteristics:</span></span>  
  
-   <span data-ttu-id="f00d0-121">Anonim yöntemler.</span><span class="sxs-lookup"><span data-stu-id="f00d0-121">Anonymous methods.</span></span> <span data-ttu-id="f00d0-122">Daha fazla bilgi için bkz: [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="f00d0-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
-   <span data-ttu-id="f00d0-123">Güvenli olmayan bloklar içeren yöntemler.</span><span class="sxs-lookup"><span data-stu-id="f00d0-123">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="f00d0-124">Daha fazla bilgi için bkz: [güvensiz](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="f00d0-124">For more information, see [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="f00d0-125">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="f00d0-125">Exception Handling</span></span>  
 <span data-ttu-id="f00d0-126">A `yield return` deyimi bir try-catch bloğu içinde bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="f00d0-126">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="f00d0-127">A `yield return` deyimi, bir try-finally deyimi try bloğunda yer alması.</span><span class="sxs-lookup"><span data-stu-id="f00d0-127">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>  
  
 <span data-ttu-id="f00d0-128">A `yield break` deyimi yer alması try blok veya bir catch bloğunun dışında bir finally bloğunda.</span><span class="sxs-lookup"><span data-stu-id="f00d0-128">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>  
  
 <span data-ttu-id="f00d0-129">Varsa `foreach` gövdesi (dışında yineleyici yöntemi) bir özel durum oluşturur bir `finally` yineleyici yöntemi bloğunda gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f00d0-129">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="f00d0-130">Teknik Uygulama</span><span class="sxs-lookup"><span data-stu-id="f00d0-130">Technical Implementation</span></span>  
 <span data-ttu-id="f00d0-131">Aşağıdaki kod döndürür bir `IEnumerable<string>` yineleyici yönteminden ve öğeleri arasında yineler.</span><span class="sxs-lookup"><span data-stu-id="f00d0-131">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 <span data-ttu-id="f00d0-132">Çağrı `MyIteratorMethod` yönteminin gövdesi yürütmez.</span><span class="sxs-lookup"><span data-stu-id="f00d0-132">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="f00d0-133">Bunun yerine çağrı döndürür bir `IEnumerable<string>` içine `elements` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="f00d0-133">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="f00d0-134">Bir yineleme `foreach` döngü, <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için çağrılır `elements`.</span><span class="sxs-lookup"><span data-stu-id="f00d0-134">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="f00d0-135">Bu çağrı gövdesini yürütür `MyIteratorMethod` sonraki kadar `yield return` deyimi ulaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="f00d0-135">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="f00d0-136">İfadesi tarafından döndürülen `yield return` ifadesi belirler değeri yalnızca `element` döngü gövdesine tüketimi için değişken aynı zamanda <xref:System.Collections.Generic.IEnumerator%601.Current%2A> özelliği `elements`, olduğu bir `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="f00d0-136">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>  
  
 <span data-ttu-id="f00d0-137">Sonraki her yinelemesinden üzerinde `foreach` nereden yürütülmeye yineleyici gövdesinin döngü ulaştığında yeniden durdurma kapalı, solda bir `yield return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f00d0-137">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="f00d0-138">`foreach` Döngüsü tamamlandıktan yineleyici yönteminin sonuna veya `yield break` deyimi ulaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="f00d0-138">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f00d0-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="f00d0-139">Example</span></span>  
 <span data-ttu-id="f00d0-140">Aşağıdaki örnek sahip bir `yield return` içinde deyimi bir `for` döngü.</span><span class="sxs-lookup"><span data-stu-id="f00d0-140">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="f00d0-141">Her yinelemesinden `foreach` deyiminin gövdesinde `Main` yöntem çağrısı oluşturur `Power` yineleyici işlevi.</span><span class="sxs-lookup"><span data-stu-id="f00d0-141">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="f00d0-142">Yineleyici işlevi her çağrısı devam eder, sonraki yürütülmesi `yield return` sonraki yinelemesini sırasında oluşur deyimi `for` döngü.</span><span class="sxs-lookup"><span data-stu-id="f00d0-142">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>  
  
 <span data-ttu-id="f00d0-143">Yineleyici yöntemin dönüş türü <xref:System.Collections.IEnumerable>, bir yineleyici arabirimi türü değil.</span><span class="sxs-lookup"><span data-stu-id="f00d0-143">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="f00d0-144">Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="f00d0-144">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="f00d0-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="f00d0-145">Example</span></span>  
 <span data-ttu-id="f00d0-146">Aşağıdaki örnekte gösterilmiştir bir `get` yineleyici olduğu erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="f00d0-146">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="f00d0-147">Örnekte, her `yield return` deyimi bir kullanıcı tarafından tanımlanan sınıfının bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f00d0-147">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f00d0-148">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f00d0-148">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f00d0-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f00d0-149">See Also</span></span>  
 [<span data-ttu-id="f00d0-150">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f00d0-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f00d0-151">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f00d0-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f00d0-152">foreach, in</span><span class="sxs-lookup"><span data-stu-id="f00d0-152">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="f00d0-153">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="f00d0-153">Iterators</span></span>](../../iterators.md)
