---
title: out parametre değiştiricisi- C# başvuru
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: bc3814b91ed4327f4af1a4a1bfbda632b0393bb8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713278"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="853ca-102">out parametresi değiştiricisi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="853ca-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="853ca-103">`out` anahtar sözcüğü, bağımsız değişkenlerin başvuruya göre geçirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="853ca-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="853ca-104">Bir değişken olması gereken, biçimsel parametreye bağımsız değişken için bir diğer ad oluşturur.</span><span class="sxs-lookup"><span data-stu-id="853ca-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="853ca-105">Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır.</span><span class="sxs-lookup"><span data-stu-id="853ca-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="853ca-106">[Ref](ref.md) anahtar sözcüğüne benzer, çünkü `ref`, değişkeninin geçirilmeden önce başlatılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="853ca-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="853ca-107">Aynı zamanda [ın](in-parameter-modifier.md) anahtar sözcüğü de gibidir, çünkü `in` bağımsız değişken değerini değiştirmek için çağrılan yönteme izin vermez.</span><span class="sxs-lookup"><span data-stu-id="853ca-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="853ca-108">Bir `out` parametresi kullanmak için, hem yöntem tanımı hem de çağıran yöntem, `out` anahtar sözcüğünü açıkça kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="853ca-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="853ca-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="853ca-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="853ca-110">`out` anahtar sözcüğü, tür parametresinin covaryant olduğunu belirtmek için genel bir tür parametresiyle de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="853ca-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="853ca-111">`out` anahtar sözcüğünün bu bağlamda kullanımı hakkında daha fazla bilgi için bkz. [Out (genel değiştirici)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="853ca-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="853ca-112">`out` bağımsız değişken olarak geçirilen değişkenlerin, yöntem çağrısında geçirilmeden önce başlatılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="853ca-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="853ca-113">Ancak, yöntemi döndürmadan önce bir değer atamak için çağrılan yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="853ca-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="853ca-114">`in`, `ref`ve `out` anahtar sözcükleri, aşırı yükleme çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="853ca-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="853ca-115">Bu nedenle, tek fark bir yöntem `ref` veya `in` bağımsız değişken alırsa ve diğeri bir `out` bağımsız değişkeni alırsa Yöntemler aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="853ca-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="853ca-116">Aşağıdaki kod, örneğin derlenmeyecektir:</span><span class="sxs-lookup"><span data-stu-id="853ca-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="853ca-117">Ancak, bir yöntem `ref`, `in`veya `out` bağımsız değişkeni alırsa ve diğeri bunun gibi bu değiştiricilerin hiçbirini içeriyorsa, aşırı yükleme geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="853ca-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="853ca-118">Derleyici, çağrı sitesindeki parametre değiştiricilerini Yöntem çağrısında kullanılan parametre değiştiricilerine eşleyerek en iyi aşırı yüklemeyi seçer.</span><span class="sxs-lookup"><span data-stu-id="853ca-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="853ca-119">Özellikler değişken değildir ve bu nedenle `out` parametresi olarak geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="853ca-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="853ca-120">Aşağıdaki tür yöntemler için `in`, `ref`ve `out` anahtar sözcüklerini kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="853ca-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="853ca-121">Zaman [uyumsuz](./async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.</span><span class="sxs-lookup"><span data-stu-id="853ca-121">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="853ca-122">Bir [yield return](./yield.md) veya `yield break` ifadesini içeren Yineleyici yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="853ca-122">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-parameters"></a><span data-ttu-id="853ca-123">`out` parametrelerini bildirme</span><span class="sxs-lookup"><span data-stu-id="853ca-123">Declaring `out` parameters</span></span>   

<span data-ttu-id="853ca-124">`out` bağımsız değişkenlerle bir yöntemi bildirmek, birden çok değer döndürmek için klasik bir geçici çözümdür.</span><span class="sxs-lookup"><span data-stu-id="853ca-124">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="853ca-125">7,0 ' C# den başlayarak, benzer senaryolar için [başlıkları](../../tuples.md) göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="853ca-125">Beginning with C# 7.0, consider [tuples](../../tuples.md) for similar scenarios.</span></span> <span data-ttu-id="853ca-126">Aşağıdaki örnek, tek bir yöntem çağrısıyla üç değişken döndürmek için `out` kullanır.</span><span class="sxs-lookup"><span data-stu-id="853ca-126">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="853ca-127">Üçüncü bağımsız değişkenin null 'a atandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="853ca-127">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="853ca-128">Bu, yöntemlerin değerleri isteğe bağlı olarak döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="853ca-128">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="853ca-129">Bir yöntemi `out` bağımsız değişkenle çağırma</span><span class="sxs-lookup"><span data-stu-id="853ca-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="853ca-130">C# 6 ve önceki sürümlerde, bir değişkeni `out` bağımsız değişken olarak geçirmeden önce ayrı bir ifadede bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="853ca-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="853ca-131">Aşağıdaki örnek, bir dizeyi bir sayıya dönüştürmeyi deneyen [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine geçirilmeden önce `number` adlı bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="853ca-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="853ca-132">C# 7,0 ' den başlayarak, `out` değişkenini ayrı bir değişken bildiriminde değil yöntem çağrısının bağımsız değişken listesinde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="853ca-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="853ca-133">Bu daha kompakt, okunabilir kod üretir ve ayrıca yöntem çağrısından önce değişkene yanlışlıkla bir değer atamaktan de engel olur.</span><span class="sxs-lookup"><span data-stu-id="853ca-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="853ca-134">Aşağıdaki örnek, [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine yapılan çağrıda `number` değişkenini tanımladığından, önceki örneğe benzer.</span><span class="sxs-lookup"><span data-stu-id="853ca-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="853ca-135">Önceki örnekte `number` değişkeni kesin olarak bir `int`olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="853ca-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="853ca-136">Ayrıca, aşağıdaki örnekte olduğu gibi örtük olarak yazılmış bir yerel değişken de bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="853ca-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="853ca-137">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="853ca-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="853ca-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="853ca-138">See also</span></span>

- [<span data-ttu-id="853ca-139">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="853ca-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="853ca-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="853ca-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="853ca-141">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="853ca-141">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="853ca-142">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="853ca-142">Method Parameters</span></span>](./method-parameters.md)
