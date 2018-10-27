---
title: parametre değiştiricisi (C# Başvurusu)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 199d2d54a1937b9982131b8cc7f1c777f656d7a9
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50049457"
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="c4327-102">parametre değiştiricisi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c4327-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="c4327-103">`in` Anahtar sözcüğü, başvuruya göre geçirilecek bağımsız değişkenleri neden olur.</span><span class="sxs-lookup"><span data-stu-id="c4327-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="c4327-104">Nasıl olduğunu [ref](ref.md) veya [kullanıma](out-parameter-modifier.md) anahtar sözcükler, tek farkı, `in` tarafından çağrılan yöntem bağımsız değişkenleri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="c4327-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="c4327-105">Oysa `ref` bağımsız değişkenleri değiştirilebilir, `out` bağımsız değişkenleri çağrılan yöntem tarafından değiştirilmelidir ve arama bağlamda observable söz konusu değişiklikler şunlardır.</span><span class="sxs-lookup"><span data-stu-id="c4327-105">Whereas `ref` arguments may be modified,  `out` arguments must be modified by the called method, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="c4327-106">Yukarıdaki örnekte gösteren `in` değiştiricisi gereksiz genellikle çağıran sitede.</span><span class="sxs-lookup"><span data-stu-id="c4327-106">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="c4327-107">Ayrıca, yöntem bildiriminde yalnızca gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c4327-107">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="c4327-108">`in` Anahtar sözcüğü de kullanılabilir bir genel tür parametresi tür parametresi değişken karşıtı, kapsamında olduğunu belirtmek için bir `foreach` deyimi veya bir parçası olarak bir `join` bir LINQ sorgu yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c4327-108">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="c4327-109">Kullanımı hakkında daha fazla bilgi için `in` anahtar sözcüğü şu bağlamlarda bkz [içinde](in.md), bu kullanan tüm bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4327-109">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
 <span data-ttu-id="c4327-110">Değişkenleri olarak geçirildi `in` bağımsız değişken bir yöntem çağrısında iletilmeden önce başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4327-110">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="c4327-111">Ancak, çağrılan yöntem olmayan bir değer atamak veya bağımsız değişkenini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c4327-111">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="c4327-112">Ancak `in`, `ref`, ve `out` anahtar sözcükleri neden farklı çalışma zamanı davranışı, derleme zamanında yöntem imzasının parçası değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="c4327-112">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="c4327-113">Tek fark, bir yöntem aldığını ise, bu nedenle, yöntemler aşırı yüklenemez bir `ref` veya `in` bağımsız değişkeni ve diğer alır bir `out` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="c4327-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="c4327-114">Örneğin, aşağıdaki kod derlemeyecektir:</span><span class="sxs-lookup"><span data-stu-id="c4327-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="c4327-115">Aşırı yükleme varlığını temel alarak `in` izin verilir:</span><span class="sxs-lookup"><span data-stu-id="c4327-115">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="c4327-116">Aşırı yükleme çözünürlüğü kuralları</span><span class="sxs-lookup"><span data-stu-id="c4327-116">Overload resolution rules</span></span>

<span data-ttu-id="c4327-117">Değer yöntemleriyle aşırı yükleme çözünürlüğü kurallarını anlamak `in` hacktivism anlama tarafından bağımsız değişkenleri `in` bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="c4327-117">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="c4327-118">Yöntemlerini kullanarak tanımlama `in` parametreleri olan bir olası performans iyileştirme.</span><span class="sxs-lookup"><span data-stu-id="c4327-118">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="c4327-119">Bazı `struct` tür bağımsız değişkenleri boyutu büyük ve yöntemler sıkı döngüler veya kritik kod yollarını çağrıldığında, bu yapıları kopyalama maliyeti önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c4327-119">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="c4327-120">Yöntemi `in` çağrılan yöntem bağımsız durumunu değiştirmez çünkü bağımsız değişkenleri başvuruya göre güvenle geçirilebilir olduğunu belirtmek için parametreleri.</span><span class="sxs-lookup"><span data-stu-id="c4327-120">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="c4327-121">Bu bağımsız değişkenleri başvuruya göre geçirme (büyük olasılıkla) pahalı kopyalama önler.</span><span class="sxs-lookup"><span data-stu-id="c4327-121">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span> 

<span data-ttu-id="c4327-122">Belirtme `in` çağrıda bağımsız değişkenler için site genellikle isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c4327-122">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="c4327-123">Bağımsız değişkenler değere göre geçirme ve başvuru kullanarak geçirme arasındaki semantik farklılığı yok `in` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="c4327-123">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="c4327-124">`in` Değiştiricisi çağrı sitesinde olduğundan isteğe bağlı bağımsız değişkenin değeri değiştirilebilir belirtmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c4327-124">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="c4327-125">Açıkça eklemeniz `in` değiştirici bağımsız değişken emin olmak için çağrı sitesinde başvuruya göre değil değere göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c4327-125">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="c4327-126">Kullanarak açıkça `in` aşağıdaki iki etkisi olur:</span><span class="sxs-lookup"><span data-stu-id="c4327-126">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="c4327-127">İlk olarak belirterek `in` çağrısı site eşleşen ile tanımlanan bir yöntem seçmek için derleyicinin zorlar `in` parametresi.</span><span class="sxs-lookup"><span data-stu-id="c4327-127">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="c4327-128">Aksi takdirde iki yöntem yalnızca içinde varken, farklı olduğunda `in`, değere göre aşırı daha iyi bir eşleşmedir.</span><span class="sxs-lookup"><span data-stu-id="c4327-128">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="c4327-129">İkinci olarak, belirtme `in` başvuruya göre bağımsız değişken geçmek için amacınız bildirir.</span><span class="sxs-lookup"><span data-stu-id="c4327-129">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="c4327-130">İle kullanılan bağımsız değişkenine `in` doğrudan başvurulabilen bir konumu temsil etmelidir.</span><span class="sxs-lookup"><span data-stu-id="c4327-130">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="c4327-131">Aynı genel kurallar için `out` ve `ref` bağımsız değişkenleri: sabitler, sıradan özellikleri veya değerler üreten diğer ifadeler kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c4327-131">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="c4327-132">Aksi takdirde, atlama `in` çağrısı salt okunur başvuru yöntemi olarak geçirmek için geçici bir değişken oluşturmak için sağlayacak site derleyici bildirir.</span><span class="sxs-lookup"><span data-stu-id="c4327-132">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="c4327-133">Derleyici ile birkaç kısıtlamaları, geçici bir değişken oluşturur `in` bağımsız değişkenleri:</span><span class="sxs-lookup"><span data-stu-id="c4327-133">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="c4327-134">Derleme zamanı sabiti olarak geçici bir değişkene izin verir `in` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="c4327-134">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="c4327-135">Özellikleri veya diğer ifadeler için geçici değişken sağlayan `in` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="c4327-135">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="c4327-136">Geçici bir değişken bağımsız değişkenleri sağlayan bir bağımsız değişken türü arasında örtük dönüşüm için parametre türü olduğu.</span><span class="sxs-lookup"><span data-stu-id="c4327-136">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="c4327-137">Tüm önceki örneklerde, derleyici sabiti, özelliği veya başka bir ifadenin değerini depolayan geçici bir değişken oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4327-137">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="c4327-138">Aşağıdaki kod bu kuralları gösterir:</span><span class="sxs-lookup"><span data-stu-id="c4327-138">The following code illustrates these rules:</span></span>

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

<span data-ttu-id="c4327-139">Şimdi, değer değişkenleriyle kullanarak başka bir yöntem yoktu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c4327-139">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="c4327-140">Sonuçları, aşağıdaki kodda gösterildiği gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c4327-140">The results change as shown in the following code:</span></span>

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

<span data-ttu-id="c4327-141">Yalnızca yöntem çağrısında bağımsız değişkenini başvuruya göre geçirildiği son sunucudur.</span><span class="sxs-lookup"><span data-stu-id="c4327-141">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="c4327-142">Önceki kod `int` kolaylık olması için bağımsız değişken türü olarak.</span><span class="sxs-lookup"><span data-stu-id="c4327-142">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="c4327-143">Çünkü `int` başvurusundan daha büyük olan en modern makineler'de, tek bir geçirme için hiçbir avantajı yoktur `int` salt okunur başvuru olarak.</span><span class="sxs-lookup"><span data-stu-id="c4327-143">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span> 

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="c4327-144">Sınırlamalar `in` parametreleri</span><span class="sxs-lookup"><span data-stu-id="c4327-144">Limitations on `in` parameters</span></span>

<span data-ttu-id="c4327-145">Kullanamazsınız `in`, `ref`, ve `out` yöntemleri aşağıdaki türde için anahtar sözcükler:</span><span class="sxs-lookup"><span data-stu-id="c4327-145">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="c4327-146">Kullanarak tanımladığınız zaman uyumsuz yöntemlerde [zaman uyumsuz](async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="c4327-146">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="c4327-147">Yineleyici yöntemleri dahil bir [yield return](yield.md) veya `yield break` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c4327-147">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="c4327-148">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="c4327-148">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c4327-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4327-149">See Also</span></span>

- [<span data-ttu-id="c4327-150">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c4327-150">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="c4327-151">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c4327-151">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="c4327-152">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c4327-152">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="c4327-153">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="c4327-153">Method Parameters</span></span>](method-parameters.md)  
- [<span data-ttu-id="c4327-154">Güvenli verimli kod yazma</span><span class="sxs-lookup"><span data-stu-id="c4327-154">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)  
