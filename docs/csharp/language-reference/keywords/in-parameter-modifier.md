---
title: parametresi değiştiricisi (C# Başvurusu)
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9b8b21e2bdc95829c831ee71f24b47986321b7d0
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="d27ce-102">parametresi değiştiricisi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d27ce-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="d27ce-103">`in` Anahtar sözcüğü başvuruya göre geçirilecek bağımsız değişkenler neden olur.</span><span class="sxs-lookup"><span data-stu-id="d27ce-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="d27ce-104">Benzer; [ref](ref.md) veya [çıkışı](out-parameter-modifier.md) anahtar sözcüklerini dışındaki `in` bağımsız değişkenleri ancak çağrılan yöntemi tarafından değiştirilemez `ref` bağımsız değişkenleri değiştirilmiş, `out` bağımsız değişkenleri çağıran tarafından değiştirilmesi gerekir ve bu değişiklik observable arama bağlamında.</span><span class="sxs-lookup"><span data-stu-id="d27ce-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method, whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="d27ce-105">Önceki örnekte gösteren `in` değiştiricisi gereksiz çağrı sitede.</span><span class="sxs-lookup"><span data-stu-id="d27ce-105">The preceding example demonstrates that the `in` modifier is unnecessary at the call site.</span></span> <span data-ttu-id="d27ce-106">Yalnızca yöntemi bildiriminde de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d27ce-106">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="d27ce-107">`in` Anahtar sözcüğü de kullanılabilir bir genel tür parametresi tür parametresi, bir parçası olarak karşıtıdır olduğunu belirtmek için bir `foreach` deyimi, veya bir parçası olarak bir `join` yan tümcesinde bir LINQ Sorgu.</span><span class="sxs-lookup"><span data-stu-id="d27ce-107">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="d27ce-108">Kullanımı hakkında daha fazla bilgi için `in` anahtar sözcüğü bu bağlamlarında bkz [içinde](in.md) Bu kullanımlar için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="d27ce-108">For more information on the use of the `in` keyword in these contexts, see [in](in.md) which provides links to all those uses.</span></span>
  
 <span data-ttu-id="d27ce-109">Değişkenler geçildi olarak `in` bağımsız değişkenleri, bir yöntem çağrısı iletilmeden önce başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d27ce-109">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="d27ce-110">Ancak, çağrılan yöntemin düzgün bir değer atamak veya bağımsız değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d27ce-110">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="d27ce-111">Ancak `in`, `ref`, ve `out` anahtar sözcükleri neden farklı bir çalışma zamanı davranışı, derleme zamanında yöntem imzası parçası değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="d27ce-111">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="d27ce-112">Bir yöntem aldığını tek fark ise, bu nedenle, yöntem aşırı yüklenemez bir `ref` veya `in` bağımsız değişkeni ve diğer alır bir `out` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d27ce-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="d27ce-113">Aşağıdaki kod, örneğin, derlenmez:</span><span class="sxs-lookup"><span data-stu-id="d27ce-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="d27ce-114">Aşırı yükleme varlığını temel `in` izin verilir, ancak derleyici uyarısı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d27ce-114">Overloading based on the presence of `in` is allowed, but generates a compiler warning:</span></span>  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

<span data-ttu-id="d27ce-115">Özellikleri veya sabitleri bayraklarıdır olarak `in` parametreleri, çünkü arama yöntemi değerlerine değişiklik yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="d27ce-115">Properties or constants may be passed as `in` parameters, because the calling method may not modify their values.</span></span>
  
<span data-ttu-id="d27ce-116">Kullanamazsınız `in`, `ref`, ve `out` yöntemleri şu tür için anahtar sözcükleri:</span><span class="sxs-lookup"><span data-stu-id="d27ce-116">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="d27ce-117">Kullanarak tanımladığınız zaman uyumsuz yöntemleri [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="d27ce-117">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
- <span data-ttu-id="d27ce-118">Dahil yineleyici metotları bir [verim return](../../../csharp/language-reference/keywords/yield.md) veya `yield break` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d27ce-118">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="d27ce-119">Genellikle bildirmelidir `in` bağımsız değişkenleri değere göre geçirme gerekli kopyalama işlemleri önlemek için bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="d27ce-119">You typically declare `in` arguments to avoid the copy operations necessary for passing arguments by value.</span></span> <span data-ttu-id="d27ce-120">Bağımsız değişkenler kopyalama işlemleri daha başvuruya göre geçirme daha pahalı olduğu değer türleri yapıları gibi olduğunda bu kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d27ce-120">This is most useful when arguments are value types such as structures where copy operations are more expensive than passing by reference.</span></span>

> [!WARNING]
>  <span data-ttu-id="d27ce-121">`in` parametreler yanlış olmadığını daha pahalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d27ce-121">`in` parameters can be even more expensive if misused.</span></span> <span data-ttu-id="d27ce-122">Derleyici üye yöntemleri yapısı durumunu değiştirirseniz bilemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d27ce-122">The compiler may not know if member methods modify the state of the struct.</span></span> <span data-ttu-id="d27ce-123">Derleyici nesne değiştirilmeyen garanti edemez her biçimde geliştirmelisiniz bir kopyasını oluşturur ve bu kopyayı kullanarak başvurular üye çağırır.</span><span class="sxs-lookup"><span data-stu-id="d27ce-123">Whenever the compiler cannot ensure that the object is not modified, it defensively creates a copy and calls member references using that copy.</span></span> <span data-ttu-id="d27ce-124">Olası değişiklikler savunma bu kopyaya ' dir.</span><span class="sxs-lookup"><span data-stu-id="d27ce-124">Any possible modifications are to that defensive copy.</span></span> <span data-ttu-id="d27ce-125">Geçirmek için bu kopyaları önlemek için iki yol olan `in` parametre olarak `in` bağımsız değişken veya yapıları olarak tanımlamak için `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="d27ce-125">The two ways to avoid these copies are to pass `in` parameters as `in` arguments or to define structures as `readonly struct`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d27ce-126">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="d27ce-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d27ce-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d27ce-127">See Also</span></span>  
 [<span data-ttu-id="d27ce-128">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d27ce-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d27ce-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d27ce-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d27ce-130">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d27ce-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d27ce-131">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="d27ce-131">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)  
 [<span data-ttu-id="d27ce-132">Başvuru semantiği ile değer türleri</span><span class="sxs-lookup"><span data-stu-id="d27ce-132">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
