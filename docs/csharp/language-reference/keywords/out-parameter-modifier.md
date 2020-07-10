---
title: out parametre değiştiricisi-C# başvurusu
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 30946c85d2b64ead3f42e03da61108fa5b367779
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174815"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="9026b-102">out parametresi değiştiricisi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9026b-102">out parameter modifier (C# Reference)</span></span>

<span data-ttu-id="9026b-103">`out`Anahtar sözcüğü, bağımsız değişkenlerin başvuruya göre geçirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="9026b-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="9026b-104">Bir değişken olması gereken, biçimsel parametreye bağımsız değişken için bir diğer ad oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9026b-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="9026b-105">Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır.</span><span class="sxs-lookup"><span data-stu-id="9026b-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="9026b-106">[Ref](ref.md) anahtar sözcüğüne benzer, ancak bu, `ref` değişkeninin geçirilmeden önce başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9026b-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="9026b-107">Aynı zamanda [ın](in-parameter-modifier.md) anahtar sözcüğüne benzer, ancak `in` çağrılan yöntemin bağımsız değişken değerini değiştirmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="9026b-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="9026b-108">Bir parametre kullanmak için `out` , hem yöntem tanımı hem de çağıran yöntemi, anahtar sözcüğünü açıkça kullanmalıdır `out` .</span><span class="sxs-lookup"><span data-stu-id="9026b-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="9026b-109">Örnek:</span><span class="sxs-lookup"><span data-stu-id="9026b-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> <span data-ttu-id="9026b-110">`out`Anahtar sözcüğü, tür parametresinin covaryant olduğunu belirtmek için genel bir tür parametresiyle de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9026b-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="9026b-111">Anahtar sözcüğünün bu bağlamda kullanımı hakkında daha fazla bilgi için `out` bkz. [Out (genel değiştirici)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="9026b-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="9026b-112">Bağımsız değişken olarak geçirilen değişkenlerin `out` , yöntem çağrısında geçirilmeden önce başlatılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9026b-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="9026b-113">Ancak, yöntemi döndürmadan önce bir değer atamak için çağrılan yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9026b-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="9026b-114">`in`, `ref` Ve `out` anahtar kelimeleri, aşırı yükleme çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="9026b-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="9026b-115">Bu nedenle, tek fark bir yöntemin bir `ref` veya bağımsız değişken alırsa `in` ve diğeri bir bağımsız değişken alırsa Yöntemler aşırı yüklenemez `out` .</span><span class="sxs-lookup"><span data-stu-id="9026b-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="9026b-116">Aşağıdaki kod, örneğin derlenmeyecektir:</span><span class="sxs-lookup"><span data-stu-id="9026b-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="9026b-117">Ancak, bir yöntem bir `ref` , `in` veya `out` bağımsız değişkeni alırsa ve diğeri bu değiştiricilerin hiçbirini içeriyorsa, bunun gibi aşırı yükleme geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="9026b-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="9026b-118">Derleyici, çağrı sitesindeki parametre değiştiricilerini Yöntem çağrısında kullanılan parametre değiştiricilerine eşleyerek en iyi aşırı yüklemeyi seçer.</span><span class="sxs-lookup"><span data-stu-id="9026b-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>

<span data-ttu-id="9026b-119">Özellikler değişken değildir ve bu nedenle parametre olarak geçirilemez `out` .</span><span class="sxs-lookup"><span data-stu-id="9026b-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="9026b-120">`in` `ref` `out` Aşağıdaki tür yöntemler için, ve anahtar sözcüklerini kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="9026b-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="9026b-121">Zaman [uyumsuz](./async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.</span><span class="sxs-lookup"><span data-stu-id="9026b-121">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="9026b-122">Bir [yield return](./yield.md) veya bildiri içeren Yineleyici yöntemleri `yield break` .</span><span class="sxs-lookup"><span data-stu-id="9026b-122">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="9026b-123">Ayrıca, [genişletme yöntemleri](../../programming-guide/classes-and-structs/extension-methods.md) aşağıdaki kısıtlamalara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9026b-123">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="9026b-124">`out`Anahtar sözcüğü, bir genişletme yönteminin ilk bağımsız değişkeninde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9026b-124">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="9026b-125">`ref`Anahtar sözcüğü, bağımsız değişken bir struct olmadığında ya da genel bir tür struct olarak kısıtlanmamışsa Genişletme yönteminin ilk bağımsız değişkeninde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9026b-125">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="9026b-126">`in`İlk bağımsız değişken bir struct olmadığı müddetçe anahtar sözcüğü kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9026b-126">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="9026b-127">`in`Anahtar sözcüğü, bir struct gibi sınırlandırsalar bile herhangi bir genel tür üzerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9026b-127">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="declaring-out-parameters"></a><span data-ttu-id="9026b-128">`out`Parametreleri bildirme</span><span class="sxs-lookup"><span data-stu-id="9026b-128">Declaring `out` parameters</span></span>

<span data-ttu-id="9026b-129">Bağımsız değişkenlerle bir yöntemi bildirmek `out` , birden çok değer döndürmek için klasik bir geçici çözümdür.</span><span class="sxs-lookup"><span data-stu-id="9026b-129">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="9026b-130">C# 7,0 ' den başlayarak benzer senaryolar için [değer tanımlama gruplarını](../builtin-types/value-tuples.md) göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9026b-130">Beginning with C# 7.0, consider [value tuples](../builtin-types/value-tuples.md) for similar scenarios.</span></span> <span data-ttu-id="9026b-131">Aşağıdaki örnek, `out` tek bir yöntem çağrısıyla üç değişken döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="9026b-131">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="9026b-132">Üçüncü bağımsız değişken null öğesine atandı.</span><span class="sxs-lookup"><span data-stu-id="9026b-132">The third argument is assigned to null.</span></span> <span data-ttu-id="9026b-133">Bu, yöntemlerin değerleri isteğe bağlı olarak döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9026b-133">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="9026b-134">Bağımsız değişkenle bir yöntemi çağırma `out`</span><span class="sxs-lookup"><span data-stu-id="9026b-134">Calling a method with an `out` argument</span></span>

<span data-ttu-id="9026b-135">C# 6 ve önceki sürümlerde, bağımsız değişken olarak geçirmeden önce bir değişkeni ayrı bir ifadede bildirmeniz gerekir `out` .</span><span class="sxs-lookup"><span data-stu-id="9026b-135">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="9026b-136">Aşağıdaki örnek, `number` bir dizeyi bir sayıya dönüştürmeyi deneyen [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine geçirilmeden önce adlı bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="9026b-136">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="9026b-137">C# 7,0 ' den başlayarak `out` değişkeni ayrı bir değişken bildiriminde değil, yöntem çağrısının bağımsız değişken listesinde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9026b-137">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="9026b-138">Bu daha kompakt, okunabilir kod üretir ve ayrıca yöntem çağrısından önce değişkene yanlışlıkla bir değer atamaktan de engel olur.</span><span class="sxs-lookup"><span data-stu-id="9026b-138">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="9026b-139">Aşağıdaki örnek, `number` [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine yapılan çağrıda değişkeni tanımladığından, önceki örneğe benzer.</span><span class="sxs-lookup"><span data-stu-id="9026b-139">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

<span data-ttu-id="9026b-140">Önceki örnekte, `number` değişken kesin olarak bir olarak yazılır `int` .</span><span class="sxs-lookup"><span data-stu-id="9026b-140">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="9026b-141">Ayrıca, aşağıdaki örnekte olduğu gibi örtük olarak yazılmış bir yerel değişken de bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9026b-141">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="9026b-142">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9026b-142">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9026b-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9026b-143">See also</span></span>

- [<span data-ttu-id="9026b-144">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9026b-144">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9026b-145">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9026b-145">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9026b-146">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9026b-146">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="9026b-147">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="9026b-147">Method Parameters</span></span>](./method-parameters.md)
