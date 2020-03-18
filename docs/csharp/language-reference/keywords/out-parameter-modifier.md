---
title: parametre değiştirici - C# Reference
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: f963188d77685bb81f7dc9fb3794e343114fe3c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173568"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="374fd-102">out parametresi değiştiricisi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="374fd-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="374fd-103">Anahtar `out` kelime bağımsız değişkenlerin başvuruyla geçirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="374fd-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="374fd-104">Bu, resmi parametreyi bağımsız değişken için bir diğer ad yapar, bu da bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="374fd-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="374fd-105">Başka bir deyişle, parametre üzerinde herhangi bir işlem bağımsız değişken üzerinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="374fd-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="374fd-106">Bu [ref](ref.md) anahtar kelime gibi, `ref` ancak bu değişken geçirilmeden önce başlatılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="374fd-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="374fd-107">Ayrıca anahtar kelime [gibi,](in-parameter-modifier.md) ancak `in` bu çağrılan yöntem bağımsız değişken değerini değiştirmek için izin vermez.</span><span class="sxs-lookup"><span data-stu-id="374fd-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="374fd-108">Bir `out` parametre kullanmak için hem yöntem tanımı hem de `out` arama yönteminin anahtar sözcüğü açıkça kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="374fd-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="374fd-109">Örnek:</span><span class="sxs-lookup"><span data-stu-id="374fd-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> <span data-ttu-id="374fd-110">`out` Anahtar kelime, tür parametresinin ortak olduğunu belirtmek için genel bir tür parametresi ile de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="374fd-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="374fd-111">Bu bağlamda `out` anahtar kelimenin kullanımı hakkında daha fazla bilgi için bkz. [out (Generic Modifier)](out-generic-modifier.md)</span><span class="sxs-lookup"><span data-stu-id="374fd-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="374fd-112">Bağımsız değişkenler `out` olarak geçirilen değişkenlerin bir yöntem çağrısında geçirilmeden önce başlatılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="374fd-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="374fd-113">Ancak, yöntem dönmeden önce bir değer atamak için çağrılan yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="374fd-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="374fd-114">, `in` `ref`ve `out` anahtar kelimeler aşırı yük çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="374fd-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="374fd-115">Bu nedenle, tek fark bir yöntemin bir `ref` bağımsız `in` değişken ilerlerken `out` diğerinin bir bağımsız değişken almasıysa, yöntemler aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="374fd-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="374fd-116">Örneğin, aşağıdaki kod derlenilmeyecektir:</span><span class="sxs-lookup"><span data-stu-id="374fd-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="374fd-117">Aşırı yükleme yasal, ancak, bir `ref`yöntem `in`alır `out` , , veya argüman ve diğer bu gibi bu değiştiriciler hiçbiri vardır:</span><span class="sxs-lookup"><span data-stu-id="374fd-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="374fd-118">Derleyici, çağrı yerindeki parametre değiştiricilerini yöntem çağrısında kullanılan parametre değiştiricileriyle eşleştirerek en iyi aşırı yüklemeyi seçer.</span><span class="sxs-lookup"><span data-stu-id="374fd-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>

<span data-ttu-id="374fd-119">Özellikler değişken değildir ve bu nedenle `out` parametre olarak geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="374fd-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="374fd-120">Aşağıdaki yöntem türleri `in`için `ref`, `out` ve anahtar kelimeleri kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="374fd-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="374fd-121">Async değiştirici kullanarak tanımladığınız [async](./async.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="374fd-121">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="374fd-122">[Verim getirisi](./yield.md) veya `yield break` deyimi içeren yineleyici yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="374fd-122">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-parameters"></a><span data-ttu-id="374fd-123">Parametreleri `out` bildirme</span><span class="sxs-lookup"><span data-stu-id="374fd-123">Declaring `out` parameters</span></span>

<span data-ttu-id="374fd-124">Bağımsız değişkenlerle `out` bir yöntem bildirmek, birden çok değer döndürmek için klasik bir geçici çözümdür.</span><span class="sxs-lookup"><span data-stu-id="374fd-124">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="374fd-125">C# 7.0 ile başlayarak, benzer senaryolar için [tuples](../../tuples.md) düşünün.</span><span class="sxs-lookup"><span data-stu-id="374fd-125">Beginning with C# 7.0, consider [tuples](../../tuples.md) for similar scenarios.</span></span> <span data-ttu-id="374fd-126">Aşağıdaki örnekte, `out` tek bir yöntem çağrısıyla üç değişken i</span><span class="sxs-lookup"><span data-stu-id="374fd-126">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="374fd-127">Üçüncü bağımsız değişkenin null olarak atandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="374fd-127">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="374fd-128">Bu, yöntemlerin değerleri isteğe bağlı olarak döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="374fd-128">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="374fd-129">Bir yöntemi `out` bağımsız değişkenle çağırma</span><span class="sxs-lookup"><span data-stu-id="374fd-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="374fd-130">C# 6 ve daha önce, bir değişkeni bağımsız değişken olarak `out` geçirmeden önce ayrı bir ifadede bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="374fd-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="374fd-131">Aşağıdaki örnek, bir dizeyi bir sayıya dönüştürmeyi amaçlayan `number` [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) yöntemine geçirilmeden önce adlı bir değişkeni bildirir.</span><span class="sxs-lookup"><span data-stu-id="374fd-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="374fd-132">C# 7.0 ile başlayarak, `out` değişkeni ayrı bir değişken bildirimi yerine yöntem çağrısının bağımsız değişken listesinde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="374fd-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="374fd-133">Bu, daha kompakt, okunabilir kod üretir ve yöntem çağrısından önce değişkene yanlışlıkla bir değer atamanızı engeller.</span><span class="sxs-lookup"><span data-stu-id="374fd-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="374fd-134">Aşağıdaki örnek, [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) `number` yöntemine yapılan çağrıdaki değişkeni tanımlaması dışında önceki örnekteki gibidir.</span><span class="sxs-lookup"><span data-stu-id="374fd-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

<span data-ttu-id="374fd-135">Önceki örnekte, `number` değişken güçlü bir şekilde `int`.</span><span class="sxs-lookup"><span data-stu-id="374fd-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="374fd-136">Aşağıdaki örnekte olduğu gibi, örtülü olarak yazılan yerel değişkeni de bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="374fd-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="374fd-137">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="374fd-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="374fd-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="374fd-138">See also</span></span>

- [<span data-ttu-id="374fd-139">C# Referans</span><span class="sxs-lookup"><span data-stu-id="374fd-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="374fd-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="374fd-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="374fd-141">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="374fd-141">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="374fd-142">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="374fd-142">Method Parameters</span></span>](./method-parameters.md)
