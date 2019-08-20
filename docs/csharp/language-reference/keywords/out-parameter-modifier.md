---
title: out parametre değiştiricisi- C# başvuru
ms.custom: seodec18
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 81d60782cf8e16d55889fb3c7c05858070a97741
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602068"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="0dd21-102">out parametresi değiştiricisi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0dd21-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="0dd21-103">Anahtar `out` sözcüğü, bağımsız değişkenlerin başvuruya göre geçirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="0dd21-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="0dd21-104">Bir değişken olması gereken, biçimsel parametreye bağımsız değişken için bir diğer ad oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0dd21-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="0dd21-105">Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır.</span><span class="sxs-lookup"><span data-stu-id="0dd21-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="0dd21-106">[Ref](ref.md) anahtar sözcüğüne benzer, ancak bu `ref` , değişkeninin geçirilmeden önce başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0dd21-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="0dd21-107">Aynı zamanda [ın](in-parameter-modifier.md) anahtar sözcüğüne benzer, ancak `in` çağrılan yöntemin bağımsız değişken değerini değiştirmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0dd21-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="0dd21-108">Bir `out` parametre kullanmak için, hem yöntem tanımı hem de çağıran yöntemi, `out` anahtar sözcüğünü açıkça kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0dd21-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="0dd21-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0dd21-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="0dd21-110">`out` Anahtar sözcüğü, tür parametresinin covaryant olduğunu belirtmek için genel bir tür parametresiyle de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0dd21-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="0dd21-111">`out` Anahtar sözcüğünün bu bağlamda kullanımı hakkında daha fazla bilgi için bkz. [Out (genel değiştirici)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="0dd21-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="0dd21-112">Bağımsız değişken olarak `out` geçirilen değişkenlerin, yöntem çağrısında geçirilmeden önce başlatılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0dd21-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="0dd21-113">Ancak, yöntemi döndürmadan önce bir değer atamak için çağrılan yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0dd21-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="0dd21-114">`in`, `ref`Ve anahtar`out` kelimeleri, aşırı yükleme çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="0dd21-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="0dd21-115">Bu nedenle, tek fark bir yöntemin bir `ref` veya `in` bağımsız değişken alırsa ve diğeri bir `out` bağımsız değişken alırsa Yöntemler aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="0dd21-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="0dd21-116">Aşağıdaki kod, örneğin derlenmeyecektir:</span><span class="sxs-lookup"><span data-stu-id="0dd21-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="0dd21-117">Ancak, bir yöntem bir `ref`, `in`veya `out` bağımsız değişkeni alırsa ve diğeri bu değiştiricilerin hiçbirini içeriyorsa, bunun gibi aşırı yükleme geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="0dd21-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="0dd21-118">Derleyici, çağrı sitesindeki parametre değiştiricilerini Yöntem çağrısında kullanılan parametre değiştiricilerine eşleyerek en iyi aşırı yüklemeyi seçer.</span><span class="sxs-lookup"><span data-stu-id="0dd21-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="0dd21-119">Özellikler değişken değildir ve bu nedenle parametre olarak `out` geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="0dd21-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="0dd21-120">Aşağıdaki tür yöntemler için `in`, `ref`ve `out` anahtar sözcüklerini kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="0dd21-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="0dd21-121">Zaman [uyumsuz](./async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.</span><span class="sxs-lookup"><span data-stu-id="0dd21-121">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="0dd21-122">Bir [yield return](./yield.md) veya `yield break` bildiri içeren Yineleyici yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="0dd21-122">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-parameters"></a><span data-ttu-id="0dd21-123">Parametreleri `out` bildirme</span><span class="sxs-lookup"><span data-stu-id="0dd21-123">Declaring `out` parameters</span></span>   

<span data-ttu-id="0dd21-124">`out` Bağımsız değişkenlerle bir yöntemi bildirmek, birden çok değer döndürmek için klasik bir geçici çözümdür.</span><span class="sxs-lookup"><span data-stu-id="0dd21-124">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="0dd21-125">7,0 ' C# den başlayarak, benzer senaryolar için [başlıkları](../../tuples.md) göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0dd21-125">Beginning with C# 7.0, consider [tuples](../../tuples.md) for similar scenarios.</span></span> <span data-ttu-id="0dd21-126">Aşağıdaki örnek, tek `out` bir yöntem çağrısıyla üç değişken döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0dd21-126">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="0dd21-127">Üçüncü bağımsız değişkenin null 'a atandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0dd21-127">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="0dd21-128">Bu, yöntemlerin değerleri isteğe bağlı olarak döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0dd21-128">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="0dd21-129">`out` Bağımsız değişkenle bir yöntemi çağırma</span><span class="sxs-lookup"><span data-stu-id="0dd21-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="0dd21-130">C# 6 ve önceki sürümlerde, `out` bağımsız değişken olarak geçirmeden önce bir değişkeni ayrı bir ifadede bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0dd21-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="0dd21-131">Aşağıdaki örnek, bir dizeyi bir sayıya `number` dönüştürmeyi deneyen [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine geçirilmeden önce adlı bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="0dd21-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="0dd21-132">C# 7,0 ' den başlayarak `out` değişkeni ayrı bir değişken bildiriminde değil, yöntem çağrısının bağımsız değişken listesinde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dd21-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="0dd21-133">Bu daha kompakt, okunabilir kod üretir ve ayrıca yöntem çağrısından önce değişkene yanlışlıkla bir değer atamaktan de engel olur.</span><span class="sxs-lookup"><span data-stu-id="0dd21-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="0dd21-134">Aşağıdaki örnek, `number` [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine yapılan çağrıda değişkeni tanımladığından, önceki örneğe benzer.</span><span class="sxs-lookup"><span data-stu-id="0dd21-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="0dd21-135">Önceki örnekte, `number` değişken kesin olarak bir `int`olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="0dd21-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="0dd21-136">Ayrıca, aşağıdaki örnekte olduğu gibi örtük olarak yazılmış bir yerel değişken de bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dd21-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="0dd21-137">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="0dd21-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0dd21-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dd21-138">See also</span></span>

- [<span data-ttu-id="0dd21-139">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="0dd21-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0dd21-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0dd21-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0dd21-141">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0dd21-141">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="0dd21-142">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="0dd21-142">Method Parameters</span></span>](./method-parameters.md)
