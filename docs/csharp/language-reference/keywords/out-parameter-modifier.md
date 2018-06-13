---
title: out parametresi değiştiricisi (C# Başvurusu)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 76c2c27d4575918bb2ed4209a7ff7d2b0517b6f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288625"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="0df8c-102">out parametresi değiştiricisi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0df8c-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="0df8c-103">`out` Anahtar sözcüğü başvuruya göre geçirilecek bağımsız değişkenler neden olur.</span><span class="sxs-lookup"><span data-stu-id="0df8c-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="0df8c-104">Benzer; [ref](ref.md) hariç anahtar sözcüğü `ref` değişkenin kendisine geçirilen önce başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0df8c-104">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="0df8c-105">Aynı zamanda gibi olan [içinde](in-parameter-modifier.md) hariç anahtar sözcüğü `in` bağımsız değişken değeri değiştirmek çağrılan yöntemine izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="0df8c-105">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="0df8c-106">Kullanılacak bir `out` parametresi, yöntem tanımı ve arama yöntemi açıkça kullanmalıdır `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="0df8c-106">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="0df8c-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0df8c-107">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="0df8c-108">`out` Anahtar sözcüğü de genel tür parametresi ile tür parametresi birlikte değişkendir olduğunu belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0df8c-108">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="0df8c-109">Kullanımı hakkında daha fazla bilgi için `out` anahtar sözcüğü bu bağlamda bkz [out (genel değiştirici)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="0df8c-109">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="0df8c-110">Değişkenler geçildi olarak `out` bağımsız bir yöntem çağrısı iletilmeden önce başlatılmış gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0df8c-110">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="0df8c-111">Ancak, çağrılan yöntemin yöntemi döndürmeden önce bir değer atamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0df8c-111">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="0df8c-112">Ancak `in`, `ref`, ve `out` anahtar sözcükleri neden farklı bir çalışma zamanı davranışı, derleme zamanında yöntem imzası parçası değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="0df8c-112">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="0df8c-113">Bir yöntem aldığını tek fark ise, bu nedenle, yöntem aşırı yüklenemez bir `ref` veya `in` bağımsız değişkeni ve diğer alır bir `out` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="0df8c-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="0df8c-114">Aşağıdaki kod, örneğin, derlenmez:</span><span class="sxs-lookup"><span data-stu-id="0df8c-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="0df8c-115">Aşırı yükleme yasal, ancak bir yöntem uzun sürerse bir `ref`, `in`, veya `out` bağımsız değişkeni ve diğer şöyle bu değiştiricileri hiçbiri sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0df8c-115">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="0df8c-116">Derleyici, yöntem çağrısında kullanılan parametre değiştiricileri çağrısı sitesinde parametre değiştiricileri eşleştirerek en iyi aşırı seçer.</span><span class="sxs-lookup"><span data-stu-id="0df8c-116">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="0df8c-117">Özellikleri değişkenleri değildir ve bu nedenle olarak gönderilemez `out` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="0df8c-117">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
 <span data-ttu-id="0df8c-118">Dizileri geçirme hakkında daha fazla bilgi için bkz: [kullanarak dizileri geçirme ref ve çıkış](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="0df8c-118">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="0df8c-119">Kullanamazsınız `in`, `ref`, ve `out` yöntemleri şu tür için anahtar sözcükleri:</span><span class="sxs-lookup"><span data-stu-id="0df8c-119">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="0df8c-120">Kullanarak tanımladığınız zaman uyumsuz yöntemleri [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="0df8c-120">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="0df8c-121">Dahil yineleyici metotları bir [verim return](../../../csharp/language-reference/keywords/yield.md) veya `yield break` deyimi.</span><span class="sxs-lookup"><span data-stu-id="0df8c-121">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="0df8c-122">Bildirme `out` bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="0df8c-122">Declaring `out` arguments</span></span>   

 <span data-ttu-id="0df8c-123">Bir yöntemle bildirme `out` bağımsız değişkenleri, birden çok değer döndürmek için bir yöntem istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0df8c-123">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="0df8c-124">Aşağıdaki örnek kullanır `out` tek yöntem çağrısı üç değişkenlerle dönün.</span><span class="sxs-lookup"><span data-stu-id="0df8c-124">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="0df8c-125">Üçüncü bağımsız değişkeni null atandığını dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0df8c-125">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="0df8c-126">Bu değer isteğe bağlı olarak döndürmek yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="0df8c-126">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 <span data-ttu-id="0df8c-127">[Deneyin düzeni](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) döndürme içerir bir `bool` bir işlem başarılı ve başarısız oldu ve değer döndürme üretilen işlemi tarafından olup olmadığını belirtmek için bir `out` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="0df8c-127">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="0df8c-128">Yöntemleri gibi ayrıştırma sayısı [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) yöntemi, bu deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="0df8c-128">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="0df8c-129">Bir yöntemi çağırma bir `out` bağımsız değişken</span><span class="sxs-lookup"><span data-stu-id="0df8c-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="0df8c-130">Olarak geçirmeden önce C# 6 ve önceki sürümlerinde, ayrı bir deyimi bir değişkene bildirmelidir bir `out` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="0df8c-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="0df8c-131">Aşağıdaki örnek adlı bir değişken bildiren `number` için geçmeden önce [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) bir dizeyi sayıya dönüştürme girişiminde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0df8c-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="0df8c-132">C# 7. 0'dan başlayarak, bildirebilirsiniz `out` değişkeni yöntem çağrısı bağımsız değişken listesi yerine ayrı bir değişken bildirimi.</span><span class="sxs-lookup"><span data-stu-id="0df8c-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="0df8c-133">Bu daha küçük, okunabilir kodunu üretir ve ayrıca yanlışlıkla bir değer değişken yöntemi çağırmadan önce atanmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="0df8c-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="0df8c-134">Tanımladığı aşağıdaki örnek önceki örnek gibi olmasıdır `number` çağrısında değişken [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0df8c-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="0df8c-135">Önceki örnekte, `number` değişken olarak belirtilmiş kesinlikle bir `int`.</span><span class="sxs-lookup"><span data-stu-id="0df8c-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="0df8c-136">Aşağıdaki örnekte olduğu gibi bir türü örtük olarak belirlenmiş yerel değişkeni de bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0df8c-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="0df8c-137">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="0df8c-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0df8c-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0df8c-138">See Also</span></span>  
 [<span data-ttu-id="0df8c-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0df8c-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0df8c-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0df8c-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0df8c-141">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0df8c-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0df8c-142">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="0df8c-142">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
