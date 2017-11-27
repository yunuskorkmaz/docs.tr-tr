---
title: "out parametresi değiştiricisi (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 68ef554f95fe71f925cfa22cc49758cec3da237e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="5556e-102">out parametresi değiştiricisi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5556e-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="5556e-103">`out` Anahtar sözcüğü başvuruya göre geçirilecek bağımsız değişkenler neden olur.</span><span class="sxs-lookup"><span data-stu-id="5556e-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="5556e-104">Benzer; [ref](../../../csharp/language-reference/keywords/ref.md) hariç anahtar sözcüğü `ref` değişkenin kendisine geçirilen önce başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5556e-104">It is like the [ref](../../../csharp/language-reference/keywords/ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="5556e-105">Kullanılacak bir `out` parametresi, yöntem tanımı ve arama yöntemi açıkça kullanmalıdır `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5556e-105">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="5556e-106">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="5556e-106">For example:</span></span>  
  
 [!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]  

> [!NOTE] 
> <span data-ttu-id="5556e-107">`out` Anahtar sözcüğü de genel tür parametresi ile tür parametresi birlikte değişkendir olduğunu belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5556e-107">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="5556e-108">Kullanımı hakkında daha fazla bilgi için `out` anahtar sözcüğü bu bağlamda bkz [out (genel değiştirici)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="5556e-108">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span></span>
  
 <span data-ttu-id="5556e-109">Değişkenler geçildi olarak `out` bağımsız bir yöntem çağrısı iletilmeden önce başlatılmış gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5556e-109">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="5556e-110">Ancak, çağrılan yöntemin yöntemi döndürmeden önce bir değer atamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5556e-110">However, the called method is required to assign a value before the method returns.</span></span>  
  
 <span data-ttu-id="5556e-111">Ancak `ref` ve `out` anahtar sözcükleri neden farklı bir çalışma zamanı davranışı, derleme zamanında yöntem imzası parçası değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="5556e-111">Although the `ref` and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="5556e-112">Bir yöntem aldığını tek fark ise, bu nedenle, yöntem aşırı yüklenemez bir `ref` bağımsız değişkeni ve diğer alır bir `out` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="5556e-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="5556e-113">Aşağıdaki kod, örneğin, derlenmez:</span><span class="sxs-lookup"><span data-stu-id="5556e-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="5556e-114">Aşırı yükleme yasal, ancak bir yöntem uzun sürerse bir `ref` veya `out` bağımsız değişkeni ve diğer şöyle hiçbiri kullanır:</span><span class="sxs-lookup"><span data-stu-id="5556e-114">Overloading is legal, however, if one method takes a `ref` or `out` argument and the other uses neither, like this:</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]  
  
 <span data-ttu-id="5556e-115">Özellikleri değişkenleri değildir ve bu nedenle olarak gönderilemez `out` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="5556e-115">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>  
  
 <span data-ttu-id="5556e-116">Dizileri geçirme hakkında daha fazla bilgi için bkz: [kullanarak dizileri geçirme ref ve çıkış](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="5556e-116">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="5556e-117">Kullanamazsınız `ref` ve `out` yöntemleri şu tür için anahtar sözcükleri:</span><span class="sxs-lookup"><span data-stu-id="5556e-117">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="5556e-118">Kullanarak tanımladığınız zaman uyumsuz yöntemleri [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5556e-118">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="5556e-119">Dahil yineleyici metotları bir [verim return](../../../csharp/language-reference/keywords/yield.md) veya `yield break` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5556e-119">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="5556e-120">Bildirme `out` bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="5556e-120">Declaring `out` arguments</span></span>   

 <span data-ttu-id="5556e-121">Bir yöntemle bildirme `out` bağımsız değişkenleri, birden çok değer döndürmek için bir yöntem istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="5556e-121">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="5556e-122">Aşağıdaki örnek kullanır `out` tek yöntem çağrısı üç değişkenlerle dönün.</span><span class="sxs-lookup"><span data-stu-id="5556e-122">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="5556e-123">Üçüncü bağımsız değişkeni null atandığını dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5556e-123">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="5556e-124">Bu değer isteğe bağlı olarak döndürmek yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5556e-124">This enables methods to return values optionally.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]  

 <span data-ttu-id="5556e-125">[Deneyin düzeni](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) döndürme içerir bir `bool` bir işlem başarılı ve başarısız oldu ve değer döndürme üretilen işlemi tarafından olup olmadığını belirtmek için bir `out` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="5556e-125">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="5556e-126">Yöntemleri gibi ayrıştırma sayısı [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) yöntemi, bu deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="5556e-126">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="5556e-127">Bir yöntemi çağırma bir `out` bağımsız değişken</span><span class="sxs-lookup"><span data-stu-id="5556e-127">Calling a method with an `out` argument</span></span>

<span data-ttu-id="5556e-128">Olarak geçirmeden önce C# 6 ve önceki sürümlerinde, ayrı bir deyimi bir değişkene bildirmelidir bir `out` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="5556e-128">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="5556e-129">Aşağıdaki örnek adlı bir değişken bildiren `number` için geçmeden önce [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) bir dizeyi sayıya dönüştürme girişiminde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5556e-129">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]  

<span data-ttu-id="5556e-130">C# 7 ile başlayan, bildirebilirsiniz `out` değişkeni yöntem çağrısı bağımsız değişken listesi yerine ayrı bir değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="5556e-130">Starting with C# 7, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="5556e-131">Bu daha küçük, okunabilir kodunu üretir ve ayrıca yanlışlıkla bir değer değişken yöntemi çağırmadan önce atanmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="5556e-131">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="5556e-132">Tanımladığı aşağıdaki örnek önceki örnek gibi olmasıdır `number` çağrısında değişken [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5556e-132">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]  
   
<span data-ttu-id="5556e-133">Önceki örnekte, `number` değişken olarak belirtilmiş kesinlikle bir `int`.</span><span class="sxs-lookup"><span data-stu-id="5556e-133">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="5556e-134">Aşağıdaki örnekte olduğu gibi bir türü örtük olarak belirlenmiş yerel değişkeni de bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5556e-134">You can also declare an implicitly typed local variable, as the following example does.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="5556e-135">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5556e-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5556e-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5556e-136">See Also</span></span>  
 [<span data-ttu-id="5556e-137">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5556e-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5556e-138">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5556e-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5556e-139">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5556e-139">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5556e-140">Yöntem parametreleri</span><span class="sxs-lookup"><span data-stu-id="5556e-140">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
