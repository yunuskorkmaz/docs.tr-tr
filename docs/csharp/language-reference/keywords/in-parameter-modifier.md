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
ms.openlocfilehash: 3c15cc0dce5b37866fd826e3d6b9adcb00724672
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="c8ab9-102">parametresi değiştiricisi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c8ab9-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="c8ab9-103">`in` Anahtar sözcüğü başvuruya göre geçirilecek bağımsız değişkenler neden olur.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="c8ab9-104">Benzer; [ref](ref.md) veya [çıkışı](out-parameter-modifier.md) anahtar sözcüklerini dışındaki `in` bağımsız değişkenleri ancak çağrılan yöntemi tarafından değiştirilemez `ref` bağımsız değişkenleri değiştirilmiş, `out` bağımsız değişkenleri çağıran tarafından değiştirilmesi gerekir ve bu değişiklik observable arama bağlamında.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method, whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="c8ab9-105">Önceki örnekte gösterilmiştir `in` değiştiricisi genellikle gereksiz çağrı sitede.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-105">The preceding example demonstrates the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="c8ab9-106">Yalnızca yöntemi bildiriminde de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-106">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="c8ab9-107">`in` Anahtar sözcüğü de kullanılabilir bir genel tür parametresi tür parametresi, bir parçası olarak karşıtıdır olduğunu belirtmek için bir `foreach` deyimi, veya bir parçası olarak bir `join` yan tümcesinde bir LINQ Sorgu.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-107">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="c8ab9-108">Kullanımı hakkında daha fazla bilgi için `in` anahtar sözcüğü bu bağlamlarında bkz [içinde](in.md), tüm bu kullanımlar için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-108">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
 <span data-ttu-id="c8ab9-109">Değişkenler geçildi olarak `in` bağımsız değişkenleri, bir yöntem çağrısı iletilmeden önce başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-109">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="c8ab9-110">Ancak, çağrılan yöntemin düzgün bir değer atamak veya bağımsız değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-110">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="c8ab9-111">Ancak `in`, `ref`, ve `out` anahtar sözcükleri neden farklı bir çalışma zamanı davranışı, derleme zamanında yöntem imzası parçası değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-111">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="c8ab9-112">Bir yöntem aldığını tek fark ise, bu nedenle, yöntem aşırı yüklenemez bir `ref` veya `in` bağımsız değişkeni ve diğer alır bir `out` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="c8ab9-113">Aşağıdaki kod, örneğin, derlenmez:</span><span class="sxs-lookup"><span data-stu-id="c8ab9-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="c8ab9-114">Aşırı yükleme varlığını temel `in` izin verilir:</span><span class="sxs-lookup"><span data-stu-id="c8ab9-114">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="c8ab9-115">Çözümleme kurallarını aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="c8ab9-115">Overload resolution rules</span></span>

<span data-ttu-id="c8ab9-116">Değeriyle yöntemleriyle aşırı çözümleme kurallarını anlama `in` gerekçesi anlama aracılığıyla bağımsız değişkenleri `in` bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-116">You can understand the overload resolution rules for methods with by value vs. `in` arguments through understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="c8ab9-117">Yöntemlerini kullanarak tanımlama `in` parametreleri olan bir olası performans en iyi duruma getirme.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-117">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="c8ab9-118">Bazı `struct` tür bağımsız değişkenleri boyutu büyük ve yöntemleri sıkı döngüler veya kritik kod yolları çağrıldığında, bu yapıları kopyalama maliyetini önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-118">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="c8ab9-119">Yöntemleri bildirmek `in` çağrılan yöntemin bağımsız durumunu değiştirmez çünkü bağımsız değişkenleri başvuruya göre güvenle geçirilebilir olduğunu belirtmek üzere parametreler.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-119">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="c8ab9-120">Bu bağımsız değişkenleri başvuruya göre geçirme (büyük olasılıkla) pahalı kopyası engeller.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-120">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span> 

<span data-ttu-id="c8ab9-121">Belirtme `in` çağrısında değişkenlerine site genellikle isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-121">Specifying `in` on arguments at the call site is typically optional.</span></span> <span data-ttu-id="c8ab9-122">Bağımsız değişkenleri değere göre geçirme ile başvuru kullanarak geçirme arasındaki anlamsal fark yoktur `in` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-122">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="c8ab9-123">`in` Çağrısı sitede değiştiricisi olduğundan isteğe bağlı bağımsız değişkeninin değeri değişebilir belirtmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-123">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="c8ab9-124">Açıkça eklemeniz `in` bağımsız değişkeni emin olmak için arama sitedeki değiştirici olmayan değere göre başvuruya göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-124">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="c8ab9-125">Açıkça kullanarak `in` iki etkilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c8ab9-125">Explicitly using `in` has two effects:</span></span>

<span data-ttu-id="c8ab9-126">İlk olarak, belirtme `in` çağrısı site eşleşen ile tanımlanmış bir yöntem seçmek için derleyici zorlar `in` parametresi.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-126">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="c8ab9-127">Aksi durumda, yalnızca içinde varken, iki yöntemleri farklı olduğunda `in`, değeriyle aşırı daha iyi bir eşleşmedir.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-127">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="c8ab9-128">İkinci olarak, belirtme `in` başvuruya göre bağımsız değişken geçirmek yapma bildirir.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-128">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="c8ab9-129">İle kullanılan bağımsız değişkenine `in` doğrudan başvuruda bulunulabilir bir konumu temsil etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-129">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="c8ab9-130">Aynı genel kurallar için `out` ve `ref` bağımsız değişkenleri uygulanır: sabitleri, normal özellikler veya değerler üretmesi diğer ifadeler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-130">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="c8ab9-131">Aksi takdirde, atlama `in` çağrısı salt okunur başvuru yöntemi olarak geçirmek için geçici bir değişken oluşturmak için sağlayacak site derleyici bildirir.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-131">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="c8ab9-132">Derleyici birkaç kısıtlamalarıyla üstesinden gelmek için geçici bir değişken oluşturur `in` bağımsız değişkenler:</span><span class="sxs-lookup"><span data-stu-id="c8ab9-132">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="c8ab9-133">Derleme zamanı sabitleri olarak geçici bir değişken verir `in` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-133">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="c8ab9-134">Özellikleri veya diğer ifadeler için geçici bir değişken sağlayan `in` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-134">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="c8ab9-135">Geçici bir değişken değişkene izin verir söz konusu olduğunda bağımsız değişken türü örtük bir dönüştürme için parametre türü.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-135">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="c8ab9-136">Tüm önceki örneklerde, derleyici sabiti, özelliği veya diğer ifade değerini depolar geçici bir değişken oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-136">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="c8ab9-137">Aşağıdaki kod, bu kurallar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c8ab9-137">The following code illustrates these rules:</span></span>

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

<span data-ttu-id="c8ab9-138">Şimdi, değer bağımsız değişken kullanarak başka bir yöntem kullanılabilir varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-138">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="c8ab9-139">Aşağıdaki kodda gösterildiği gibi değişiklik sonuçları:</span><span class="sxs-lookup"><span data-stu-id="c8ab9-139">The results change as shown in the following code:</span></span>

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

<span data-ttu-id="c8ab9-140">Başvuruya göre bağımsız değişken geçirildiği yalnızca yöntem çağrısı son sunucudur.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-140">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="c8ab9-141">Önceki kod kullanan `int` Basitlik bağımsız değişken türü olarak.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-141">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="c8ab9-142">Çünkü `int` başvurusundan daha büyük olan çoğu modern makinelerinizde tek bir geçirme hiçbir faydası yoktur `int` salt okunur başvuru olarak.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-142">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span> 

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="c8ab9-143">Sınırlamalar `in` parametreleri</span><span class="sxs-lookup"><span data-stu-id="c8ab9-143">Limitations on `in` parameters</span></span>

<span data-ttu-id="c8ab9-144">Kullanamazsınız `in`, `ref`, ve `out` yöntemleri şu tür için anahtar sözcükleri:</span><span class="sxs-lookup"><span data-stu-id="c8ab9-144">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="c8ab9-145">Kullanarak tanımladığınız zaman uyumsuz yöntemleri [zaman uyumsuz](async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-145">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="c8ab9-146">Dahil yineleyici metotları bir [verim return](yield.md) veya `yield break` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-146">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="c8ab9-147">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="c8ab9-147">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c8ab9-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c8ab9-148">See Also</span></span>  
 [<span data-ttu-id="c8ab9-149">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c8ab9-149">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="c8ab9-150">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c8ab9-150">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="c8ab9-151">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c8ab9-151">C# Keywords</span></span>](index.md)  
 <span data-ttu-id="c8ab9-152">[Yöntem parametreleri](method-parameters.md) [başvuru semantiği ile değer türleri](../../reference-semantics-with-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="c8ab9-152">[Method Parameters](method-parameters.md) [Reference Semantics with Value Types](../../reference-semantics-with-value-types.md)</span></span>
