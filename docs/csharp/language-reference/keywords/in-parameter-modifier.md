---
description: parametre değiştiricisi-C# başvurusu
title: parametre değiştiricisi-C# başvurusu
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: b9cd308a1eaf2ae8f4e3e89b1a4770933b3978cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91188414"
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="fbcb6-103">parametre değiştiricide (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fbcb6-103">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="fbcb6-104">`in`Anahtar sözcüğü, bağımsız değişkenlerin başvuruya göre geçirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-104">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="fbcb6-105">Bir değişken olması gereken, biçimsel parametreye bağımsız değişken için bir diğer ad oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-105">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="fbcb6-106">Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-106">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="fbcb6-107">[Başvuru](ref.md) veya [Çıkış](out-parameter-modifier.md) anahtar kelimeleri gibidir, bu `in` bağımsız değişkenler çağrılan yöntem tarafından değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-107">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="fbcb6-108">`ref`Bağımsız değişkenler değiştirilebilir, `out` bağımsız değişkenler çağrılan yöntemle değiştirilmelidir ve bu değişiklikler çağıran bağlamda Observable ' tır.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-108">Whereas `ref` arguments may be modified, `out` arguments must be modified by the called method, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="fbcb6-109">Yukarıdaki örnek, `in` değiştiricinin çağrı sitesinde genellikle gereksiz olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-109">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="fbcb6-110">Yalnızca yöntem bildiriminde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-110">It is only required in the method declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="fbcb6-111">`in`Anahtar sözcüğü, tür parametresinin değişken karşıtı olduğunu, bir deyimin parçası olarak `foreach` veya bir `join` LINQ sorgusundaki yan tümcesinin bir parçası olarak belirtmek için genel bir tür parametresiyle de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-111">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="fbcb6-112">Bu bağlamlarda anahtar sözcüğünün kullanımı hakkında daha fazla bilgi için, `in` bkz. [içindeki](in.md)tüm kullanımları için bağlantı sağlayan.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-112">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
<span data-ttu-id="fbcb6-113">Bağımsız değişken olarak geçirilen değişkenlerin `in` bir yöntem çağrısında geçirilmeden önce başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-113">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="fbcb6-114">Ancak çağrılan yöntem bir değer atayamayabilir veya bağımsız değişkeni değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-114">However, the called method may not assign a value or modify the argument.</span></span>  

<span data-ttu-id="fbcb6-115">`in`Parametre değiştiricisi C# 7,2 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-115">The `in` parameter modifier is available in C# 7.2 and later.</span></span> <span data-ttu-id="fbcb6-116">Önceki sürümlerde derleyici hatası `CS8107` ("' ReadOnly başvuruları" özelliği C# 7,0 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-116">Previous versions generate compiler error `CS8107` ("Feature 'readonly references' is not available in C# 7.0.</span></span> <span data-ttu-id="fbcb6-117">Lütfen dil sürümü 7,2 veya üstünü kullanın. ") Derleyici dili sürümünü yapılandırmak için bkz. [C# dil sürümünü seçme](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="fbcb6-117">Please use language version 7.2 or greater.") To configure the compiler language version, see [Select the C# language version](../configure-language-version.md).</span></span>

<span data-ttu-id="fbcb6-118">`in`, `ref` Ve `out` anahtar kelimeleri, aşırı yükleme çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-118">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="fbcb6-119">Bu nedenle, tek fark bir yöntemin bir `ref` veya bağımsız değişken alırsa `in` ve diğeri bir bağımsız değişken alırsa Yöntemler aşırı yüklenemez `out` .</span><span class="sxs-lookup"><span data-stu-id="fbcb6-119">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="fbcb6-120">Aşağıdaki kod, örneğin derlenmeyecektir:</span><span class="sxs-lookup"><span data-stu-id="fbcb6-120">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="fbcb6-121">Varlığına göre aşırı yüklemeye `in` izin verilir:</span><span class="sxs-lookup"><span data-stu-id="fbcb6-121">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="fbcb6-122">Aşırı yükleme çözümleme kuralları</span><span class="sxs-lookup"><span data-stu-id="fbcb6-122">Overload resolution rules</span></span>

<span data-ttu-id="fbcb6-123">`in`Bağımsız değişkenler için mosyon 'yı anlayarak değere ve bağımsız değişkenlerle ile yöntemler için aşırı yükleme çözümleme kurallarını anlayabilirsiniz `in` .</span><span class="sxs-lookup"><span data-stu-id="fbcb6-123">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="fbcb6-124">Parametreleri kullanarak yöntemlerin tanımlanması `in` potansiyel bir performans iyileştirmesidir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-124">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="fbcb6-125">Bazı `struct` tür bağımsız değişkenleri boyutu büyük olabilir ve Yöntemler sıkı Döngülerde veya kritik kod yollarında çağrıldığında, bu yapıları kopyalama maliyeti kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-125">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="fbcb6-126">Yöntemler, bu `in` bağımsız değişkenin durumunu değiştirmediğinden bağımsız değişkenlerin başvuruya güvenli bir şekilde geçirilebileceğini belirtmek için parametreler bildirir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-126">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="fbcb6-127">Bu bağımsız değişkenlerin başvuruya göre geçirilmesi, (potansiyel) pahalı kopyayı önler.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-127">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span>

<span data-ttu-id="fbcb6-128">`in`Çağrı sitesinde bağımsız değişkenlerin belirtilmesi genellikle isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-128">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="fbcb6-129">Bağımsız değişkenleri değere göre geçirme ve değiştiricisini kullanarak başvuruya göre geçirme arasında herhangi bir semantik fark yoktur `in` .</span><span class="sxs-lookup"><span data-stu-id="fbcb6-129">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="fbcb6-130">`in`Bağımsız değişkenin değerinin değiştirilip değiştirilemeyeceğini belirtmeniz gerekmiyorsa, çağrı sitesindeki değiştirici isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-130">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="fbcb6-131">`in`Bağımsız değişkenin değere göre değil başvuruya göre geçirildiğinden emin olmak için çağrı sitesine açıkça değiştiricisini eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-131">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="fbcb6-132">Açıkça kullanmak `in` aşağıdaki iki etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="fbcb6-132">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="fbcb6-133">İlk olarak, `in` çağıran sitede belirtme, derleyicinin eşleşen bir parametreyle tanımlanmış bir yöntemi seçmesini zorlar `in` .</span><span class="sxs-lookup"><span data-stu-id="fbcb6-133">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="fbcb6-134">Aksi takdirde, iki yöntem yalnızca varlığı içinde farklılık gösteriyorsa `in` , bu değer aşırı yükleme daha iyi bir eşleşmedir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-134">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="fbcb6-135">İkincisi, belirtme, `in` bir bağımsız değişkeni başvuruya göre geçirme amacınızı bildirir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-135">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="fbcb6-136">İle kullanılan bağımsız değişken, `in` doğrudan başvuruda bulunulabilir bir konumu temsil etmelidir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-136">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="fbcb6-137">Ve bağımsız değişkenler için aynı genel kurallar `out` `ref` geçerlidir: sabitleri, olağan özellikleri veya değer üreten diğer ifadeleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-137">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="fbcb6-138">Aksi takdirde, `in` çağıran sitede atlama yöntemi derleyiciye bildirir ve bu, yönteme salt okuma başvurusu ile geçirilecek geçici bir değişken oluşturmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-138">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="fbcb6-139">Derleyici, bağımsız değişkenlerle birkaç kısıtlamayı aşmak için geçici bir değişken oluşturur `in` :</span><span class="sxs-lookup"><span data-stu-id="fbcb6-139">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="fbcb6-140">Geçici bir değişken, derleme zamanı sabitlerinin parametre olarak kullanılmasına izin verir `in` .</span><span class="sxs-lookup"><span data-stu-id="fbcb6-140">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="fbcb6-141">Geçici bir değişken özellikler veya parametreler için diğer ifadelere izin verir `in` .</span><span class="sxs-lookup"><span data-stu-id="fbcb6-141">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="fbcb6-142">Geçici bir değişken, bağımsız değişken türünden parametre türüne örtük bir dönüştürme olduğu bağımsız değişkenlere izin verir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-142">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="fbcb6-143">Önceki tüm örneklerde, derleyici sabit, özellik veya başka bir ifadenin değerini depolayan geçici bir değişken oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-143">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="fbcb6-144">Aşağıdaki kod bu kuralları gösterir:</span><span class="sxs-lookup"><span data-stu-id="fbcb6-144">The following code illustrates these rules:</span></span>

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

<span data-ttu-id="fbcb6-145">Şimdi, değer bağımsız değişkenlerine göre kullanılan başka bir yöntem bulunduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-145">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="fbcb6-146">Sonuçlar aşağıdaki kodda gösterildiği gibi değişir:</span><span class="sxs-lookup"><span data-stu-id="fbcb6-146">The results change as shown in the following code:</span></span>

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

<span data-ttu-id="fbcb6-147">Bağımsız değişkenin başvuruya göre geçirildiği tek yöntem çağrısı son bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-147">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="fbcb6-148">Önceki kod `int` basitlik için bağımsız değişken türü olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-148">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="fbcb6-149">`int`Çoğu modern makinenin bir başvurusundan daha büyük olmadığından, tek tek bir `int` salt okunur başvuru olarak geçirilme avantajı yoktur.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-149">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span>

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="fbcb6-150">Parametrelerle ilgili sınırlamalar `in`</span><span class="sxs-lookup"><span data-stu-id="fbcb6-150">Limitations on `in` parameters</span></span>

<span data-ttu-id="fbcb6-151">`in` `ref` `out` Aşağıdaki tür yöntemler için, ve anahtar sözcüklerini kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="fbcb6-151">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="fbcb6-152">Zaman [uyumsuz](async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-152">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="fbcb6-153">Bir [yield return](yield.md) veya bildiri içeren Yineleyici yöntemleri `yield break` .</span><span class="sxs-lookup"><span data-stu-id="fbcb6-153">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>
- <span data-ttu-id="fbcb6-154">Uzantı yönteminin ilk bağımsız değişkeni, `in` Bu bağımsız değişken bir struct olmadığı takdirde değiştiriciye sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-154">The first argument of an extension method cannot have the `in` modifier unless that argument is a struct.</span></span>
- <span data-ttu-id="fbcb6-155">Bu bağımsız değişkenin genel bir tür olduğu bir genişletme yönteminin ilk bağımsız değişkeni (Bu tür bir struct gibi kısıtlanıyor olsa bile).</span><span class="sxs-lookup"><span data-stu-id="fbcb6-155">The first argument of an extension method where that argument is a generic type (even when that type is constrained to be a struct.)</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fbcb6-156">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="fbcb6-156">C# Language Specification</span></span>  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fbcb6-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbcb6-157">See also</span></span>

- [<span data-ttu-id="fbcb6-158">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fbcb6-158">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fbcb6-159">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fbcb6-159">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fbcb6-160">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fbcb6-160">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fbcb6-161">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="fbcb6-161">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="fbcb6-162">Güvenli verimli kod yazma</span><span class="sxs-lookup"><span data-stu-id="fbcb6-162">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
