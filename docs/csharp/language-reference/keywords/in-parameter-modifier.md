---
title: parametre değiştirici- C# başvuru
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 10e7b91f9a6bf280c5f0654b243492bac8cde1e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715247"
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="7a423-102">parametre değiştiricide (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="7a423-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="7a423-103">`in` anahtar sözcüğü, bağımsız değişkenlerin başvuruya göre geçirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="7a423-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="7a423-104">Bir değişken olması gereken, biçimsel parametreye bağımsız değişken için bir diğer ad oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7a423-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="7a423-105">Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır.</span><span class="sxs-lookup"><span data-stu-id="7a423-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="7a423-106">`in` bağımsız değişkenleri, çağrılan yöntem tarafından değiştirilemediği için [ref](ref.md) veya [Out](out-parameter-modifier.md) anahtar kelimeleri gibidir.</span><span class="sxs-lookup"><span data-stu-id="7a423-106">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="7a423-107">`ref` bağımsız değişkenler değiştirilebilir, `out` bağımsız değişkenler çağrılan yöntemle değiştirilmelidir ve bu değişiklikler çağıran bağlamda observable olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7a423-107">Whereas `ref` arguments may be modified, `out` arguments must be modified by the called method, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="7a423-108">Yukarıdaki örnek, `in` değiştiricinin çağrı sitesinde genellikle gereksiz olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a423-108">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="7a423-109">Yalnızca yöntem bildiriminde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7a423-109">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="7a423-110">`in` anahtar sözcüğü, tür parametresinin değişken karşıtı olduğunu, `foreach` bildiriminin bir parçası olarak veya bir LINQ sorgusunda `join` yan tümcesinin bir parçası olarak belirtmek için genel bir tür parametresiyle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7a423-110">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="7a423-111">Bu bağlamlarda `in` anahtar sözcüğünün kullanımı hakkında daha fazla bilgi için, bkz. [içindeki](in.md)tüm kullanımlar için bağlantı sağlayan.</span><span class="sxs-lookup"><span data-stu-id="7a423-111">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
<span data-ttu-id="7a423-112">`in` bağımsız değişken olarak geçirilen değişkenlerin bir yöntem çağrısında geçirilmeden önce başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7a423-112">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="7a423-113">Ancak çağrılan yöntem bir değer atayamayabilir veya bağımsız değişkeni değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="7a423-113">However, the called method may not assign a value or modify the argument.</span></span>  

<span data-ttu-id="7a423-114">`in` parametre değiştiricisi C# 7,2 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7a423-114">The `in` parameter modifier is available in C# 7.2 and later.</span></span> <span data-ttu-id="7a423-115">Önceki sürümler derleyici hatası oluşturur `CS8107` ("özellik ' ReadOnly başvurular ' 7,0 içinde C# kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7a423-115">Previous versions generate compiler error `CS8107` ("Feature 'readonly references' is not available in C# 7.0.</span></span> <span data-ttu-id="7a423-116">Lütfen dil sürümü 7,2 veya üstünü kullanın. ") Derleyici dili sürümünü yapılandırmak için bkz. [ C# dil sürümünü seçme](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="7a423-116">Please use language version 7.2 or greater.") To configure the compiler language version, see [Select the C# language version](../configure-language-version.md).</span></span>

<span data-ttu-id="7a423-117">`in`, `ref`ve `out` anahtar sözcükleri, aşırı yükleme çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="7a423-117">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="7a423-118">Bu nedenle, tek fark bir yöntem `ref` veya `in` bağımsız değişken alırsa ve diğeri bir `out` bağımsız değişkeni alırsa Yöntemler aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="7a423-118">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="7a423-119">Aşağıdaki kod, örneğin derlenmeyecektir:</span><span class="sxs-lookup"><span data-stu-id="7a423-119">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="7a423-120">`in` varlığına göre aşırı yüklemeye izin verilir:</span><span class="sxs-lookup"><span data-stu-id="7a423-120">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="7a423-121">Aşırı yükleme çözümleme kuralları</span><span class="sxs-lookup"><span data-stu-id="7a423-121">Overload resolution rules</span></span>

<span data-ttu-id="7a423-122">`in` bağımsız değişkenler için mosyon 'yı anlayarak, değere ve `in` bağımsız değişkenlerine sahip yöntemler için aşırı yükleme çözümleme kurallarını anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a423-122">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="7a423-123">`in` parametrelerini kullanarak yöntemlerin tanımlanması potansiyel bir performans iyileştirmesidir.</span><span class="sxs-lookup"><span data-stu-id="7a423-123">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="7a423-124">Bazı `struct` tür bağımsız değişkenleri boyutu büyük olabilir ve Yöntemler sıkı Döngülerde veya kritik kod yollarında çağrıldığında, bu yapıları kopyalama maliyeti kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7a423-124">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="7a423-125">Yöntemler bu bağımsız değişken durumunu değiştirmediğinden bağımsız değişkenlerin başvuruya güvenli bir şekilde geçirilebileceğini belirtmek için `in` parametrelerini bildirir.</span><span class="sxs-lookup"><span data-stu-id="7a423-125">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="7a423-126">Bu bağımsız değişkenlerin başvuruya göre geçirilmesi, (potansiyel) pahalı kopyayı önler.</span><span class="sxs-lookup"><span data-stu-id="7a423-126">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span> 

<span data-ttu-id="7a423-127">Çağrı sitesinde bağımsız değişkenler için `in` belirtmek genellikle isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7a423-127">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="7a423-128">Bağımsız değişkenleri değere göre geçirme ve `in` değiştiricisini kullanarak başvuruya göre geçirme arasında herhangi bir semantik fark yoktur.</span><span class="sxs-lookup"><span data-stu-id="7a423-128">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="7a423-129">Bağımsız değişkenin değerinin değiştirilip değiştirilemeyeceğini belirtmeniz gerekmiyorsa, çağrı sitesindeki `in` değiştiricisi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7a423-129">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="7a423-130">Bağımsız değişkenin değere göre değil başvuruya göre geçirildiğinden emin olmak için çağrı sitesine `in` değiştiricisini açıkça eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="7a423-130">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="7a423-131">Açıkça `in` kullanımı aşağıdaki iki etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7a423-131">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="7a423-132">İlk olarak, çağıran sitede `in` belirttiğinizde, derleyicinin eşleşen bir `in` parametresiyle tanımlanmış bir yöntemi seçmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="7a423-132">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="7a423-133">Aksi takdirde, iki yöntem yalnızca `in`olduğunda farklılık gösteriyorsa, değer aşırı yüklemesi daha iyi bir eşleşmedir.</span><span class="sxs-lookup"><span data-stu-id="7a423-133">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="7a423-134">İkincisi, `in` belirtmek için bir bağımsız değişkeni başvuruya göre geçirme amacınızı bildirir.</span><span class="sxs-lookup"><span data-stu-id="7a423-134">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="7a423-135">`in` ile kullanılan bağımsız değişken, doğrudan başvuruda bulunulabilir bir konumu temsil etmelidir.</span><span class="sxs-lookup"><span data-stu-id="7a423-135">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="7a423-136">`out` ve `ref` bağımsız değişkenleri için aynı genel kurallar geçerlidir: sabitleri, olağan özellikleri veya değer üreten diğer ifadeleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7a423-136">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="7a423-137">Aksi takdirde, çağrı sitesindeki `in` atlanması derleyiciye bildirir ve bu, yönteme salt okuma başvurusu ile geçirilecek geçici bir değişken oluşturmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="7a423-137">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="7a423-138">Derleyici, `in` bağımsız değişkenlerle çeşitli kısıtlamaları aşmak için geçici bir değişken oluşturur:</span><span class="sxs-lookup"><span data-stu-id="7a423-138">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="7a423-139">Geçici bir değişken, `in` parametre olarak derleme zamanı sabitlerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="7a423-139">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="7a423-140">Geçici bir değişken özellikler veya `in` parametrelere yönelik diğer ifadelere izin verir.</span><span class="sxs-lookup"><span data-stu-id="7a423-140">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="7a423-141">Geçici bir değişken, bağımsız değişken türünden parametre türüne örtük bir dönüştürme olduğu bağımsız değişkenlere izin verir.</span><span class="sxs-lookup"><span data-stu-id="7a423-141">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="7a423-142">Önceki tüm örneklerde, derleyici sabit, özellik veya başka bir ifadenin değerini depolayan geçici bir değişken oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7a423-142">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="7a423-143">Aşağıdaki kod bu kuralları gösterir:</span><span class="sxs-lookup"><span data-stu-id="7a423-143">The following code illustrates these rules:</span></span>

```csharp
static void Method(in int argument)
{
    // implementation removed
}

Method(5); // OK, temporary variable created.
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // OK, temporary int created with the value 0
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // passed by readonly reference
Method(in i); // passed by readonly reference, explicitly using `in`
```

<span data-ttu-id="7a423-144">Şimdi, değer bağımsız değişkenlerine göre kullanılan başka bir yöntem bulunduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7a423-144">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="7a423-145">Sonuçlar aşağıdaki kodda gösterildiği gibi değişir:</span><span class="sxs-lookup"><span data-stu-id="7a423-145">The results change as shown in the following code:</span></span>

```csharp
static void Method(int argument)
{
    // implementation removed
}

static void Method(in int argument)
{
    // implementation removed
}

Method(5); // Calls overload passed by value
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // Calls overload passed by value.
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // Calls overload passed by value
Method(in i); // passed by readonly reference, explicitly using `in`
```

<span data-ttu-id="7a423-146">Bağımsız değişkenin başvuruya göre geçirildiği tek yöntem çağrısı son bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="7a423-146">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="7a423-147">Yukarıdaki kod basitlik için bağımsız değişken türü olarak `int` kullanır.</span><span class="sxs-lookup"><span data-stu-id="7a423-147">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="7a423-148">`int` çoğu modern makinelerdeki bir başvurudan daha büyük olmadığından, tek bir `int` salt okunur başvuru olarak geçirilmesi avantajına sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="7a423-148">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span> 

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="7a423-149">`in` parametrelerinin sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="7a423-149">Limitations on `in` parameters</span></span>

<span data-ttu-id="7a423-150">Aşağıdaki tür yöntemler için `in`, `ref`ve `out` anahtar sözcüklerini kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="7a423-150">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="7a423-151">Zaman [uyumsuz](async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.</span><span class="sxs-lookup"><span data-stu-id="7a423-151">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="7a423-152">Bir [yield return](yield.md) veya `yield break` ifadesini içeren Yineleyici yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="7a423-152">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="7a423-153">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="7a423-153">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7a423-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a423-154">See also</span></span>

- [<span data-ttu-id="7a423-155">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="7a423-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7a423-156">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7a423-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7a423-157">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="7a423-157">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7a423-158">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="7a423-158">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="7a423-159">Güvenli verimli kod yazma</span><span class="sxs-lookup"><span data-stu-id="7a423-159">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
