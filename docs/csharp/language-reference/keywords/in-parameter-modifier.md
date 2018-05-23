---
title: parametresi değiştiricisi (C# Başvurusu)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 58500cf2caa1446af6b663f1b765c0be92309f1d
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="e1ddc-102">parametresi değiştiricisi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e1ddc-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="e1ddc-103">`in` Anahtar sözcüğü başvuruya göre geçirilecek bağımsız değişkenler neden olur.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="e1ddc-104">Benzer; [ref](ref.md) veya [çıkışı](out-parameter-modifier.md) anahtar sözcüklerini dışındaki `in` bağımsız değişkenleri çağrılan yöntemi tarafından değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="e1ddc-105">Oysa `ref` bağımsız değişkenleri değiştirilmiş, `out` bağımsız değişkenleri çağıran tarafından değiştirilmesi gerekir ve bu değişiklik observable arama bağlamında olan.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-105">Whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="e1ddc-106">Önceki örnekte gösteren `in` değiştiricisi genellikle gereksiz çağrı sitede.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-106">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="e1ddc-107">Yalnızca yöntemi bildiriminde de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-107">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="e1ddc-108">`in` Anahtar sözcüğü de kullanılabilir bir genel tür parametresi tür parametresi, bir parçası olarak karşıtıdır olduğunu belirtmek için bir `foreach` deyimi, veya bir parçası olarak bir `join` yan tümcesinde bir LINQ Sorgu.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-108">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="e1ddc-109">Kullanımı hakkında daha fazla bilgi için `in` anahtar sözcüğü bu bağlamlarında bkz [içinde](in.md), tüm bu kullanımlar için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-109">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
 <span data-ttu-id="e1ddc-110">Değişkenler geçildi olarak `in` bağımsız değişkenleri, bir yöntem çağrısı iletilmeden önce başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-110">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="e1ddc-111">Ancak, çağrılan yöntemin düzgün bir değer atamak veya bağımsız değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-111">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="e1ddc-112">Ancak `in`, `ref`, ve `out` anahtar sözcükleri neden farklı bir çalışma zamanı davranışı, derleme zamanında yöntem imzası parçası değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-112">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="e1ddc-113">Bir yöntem aldığını tek fark ise, bu nedenle, yöntem aşırı yüklenemez bir `ref` veya `in` bağımsız değişkeni ve diğer alır bir `out` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="e1ddc-114">Aşağıdaki kod, örneğin, derlenmez:</span><span class="sxs-lookup"><span data-stu-id="e1ddc-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="e1ddc-115">Aşırı yükleme varlığını temel `in` izin verilir:</span><span class="sxs-lookup"><span data-stu-id="e1ddc-115">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="e1ddc-116">Çözümleme kurallarını aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="e1ddc-116">Overload resolution rules</span></span>

<span data-ttu-id="e1ddc-117">Değeriyle yöntemleriyle aşırı çözümleme kurallarını anlama `in` gerekçesi anlama tarafından bağımsız değişkenleri `in` bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-117">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="e1ddc-118">Yöntemlerini kullanarak tanımlama `in` parametreleri olan bir olası performans en iyi duruma getirme.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-118">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="e1ddc-119">Bazı `struct` tür bağımsız değişkenleri boyutu büyük ve yöntemleri sıkı döngüler veya kritik kod yolları çağrıldığında, bu yapıları kopyalama maliyetini önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-119">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="e1ddc-120">Yöntemleri bildirmek `in` çağrılan yöntemin bağımsız durumunu değiştirmez çünkü bağımsız değişkenleri başvuruya göre güvenle geçirilebilir olduğunu belirtmek üzere parametreler.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-120">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="e1ddc-121">Bu bağımsız değişkenleri başvuruya göre geçirme (büyük olasılıkla) pahalı kopyası engeller.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-121">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span> 

<span data-ttu-id="e1ddc-122">Belirtme `in` çağrısında bağımsız değişkenler için site genellikle isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-122">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="e1ddc-123">Bağımsız değişkenleri değere göre geçirme ile başvuru kullanarak geçirme arasındaki anlamsal fark yoktur `in` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-123">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="e1ddc-124">`in` Çağrısı sitede değiştiricisi olduğundan isteğe bağlı bağımsız değişkeninin değeri değişebilir belirtmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-124">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="e1ddc-125">Açıkça eklemeniz `in` bağımsız değişkeni emin olmak için arama sitedeki değiştirici olmayan değere göre başvuruya göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-125">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="e1ddc-126">Açıkça kullanarak `in` aşağıdaki iki etkilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e1ddc-126">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="e1ddc-127">İlk olarak, belirtme `in` çağrısı site eşleşen ile tanımlanmış bir yöntem seçmek için derleyici zorlar `in` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-127">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="e1ddc-128">Aksi durumda, yalnızca içinde varken, iki yöntemleri farklı olduğunda `in`, değeriyle aşırı daha iyi bir eşleşmedir.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-128">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="e1ddc-129">İkinci olarak, belirtme `in` başvuruya göre bağımsız değişken geçirmek yapma bildirir.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-129">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="e1ddc-130">İle kullanılan bağımsız değişkenine `in` doğrudan başvuruda bulunulabilir bir konumu temsil etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-130">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="e1ddc-131">Aynı genel kurallar için `out` ve `ref` bağımsız değişkenleri uygulanır: sabitleri, normal özellikler veya değerler üretmesi diğer ifadeler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-131">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="e1ddc-132">Aksi takdirde, atlama `in` çağrısı salt okunur başvuru yöntemi olarak geçirmek için geçici bir değişken oluşturmak için sağlayacak site derleyici bildirir.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-132">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="e1ddc-133">Derleyici birkaç kısıtlamalarıyla üstesinden gelmek için geçici bir değişken oluşturur `in` bağımsız değişkenler:</span><span class="sxs-lookup"><span data-stu-id="e1ddc-133">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="e1ddc-134">Derleme zamanı sabitleri olarak geçici bir değişken verir `in` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-134">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="e1ddc-135">Özellikleri veya diğer ifadeler için geçici bir değişken sağlayan `in` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-135">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="e1ddc-136">Geçici bir değişken değişkene izin verir söz konusu olduğunda bağımsız değişken türü örtük bir dönüştürme için parametre türü.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-136">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="e1ddc-137">Tüm önceki örneklerde, derleyici sabiti, özelliği veya diğer ifade değerini depolar geçici bir değişken oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-137">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="e1ddc-138">Aşağıdaki kod, bu kurallar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e1ddc-138">The following code illustrates these rules:</span></span>

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

<span data-ttu-id="e1ddc-139">Şimdi, değer bağımsız değişken kullanarak başka bir yöntem kullanılabilir varsayalım.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-139">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="e1ddc-140">Aşağıdaki kodda gösterildiği gibi değişiklik sonuçları:</span><span class="sxs-lookup"><span data-stu-id="e1ddc-140">The results change as shown in the following code:</span></span>

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

<span data-ttu-id="e1ddc-141">Başvuruya göre bağımsız değişken geçirildiği yalnızca yöntem çağrısı son sunucudur.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-141">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="e1ddc-142">Önceki kod kullanan `int` Basitlik bağımsız değişken türü olarak.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-142">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="e1ddc-143">Çünkü `int` başvurusundan daha büyük olan çoğu modern makinelerinizde tek bir geçirme hiçbir faydası yoktur `int` salt okunur başvuru olarak.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-143">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span> 

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="e1ddc-144">Sınırlamalar `in` parametreleri</span><span class="sxs-lookup"><span data-stu-id="e1ddc-144">Limitations on `in` parameters</span></span>

<span data-ttu-id="e1ddc-145">Kullanamazsınız `in`, `ref`, ve `out` yöntemleri şu tür için anahtar sözcükleri:</span><span class="sxs-lookup"><span data-stu-id="e1ddc-145">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="e1ddc-146">Kullanarak tanımladığınız zaman uyumsuz yöntemleri [zaman uyumsuz](async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-146">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="e1ddc-147">Dahil yineleyici metotları bir [verim return](yield.md) veya `yield break` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-147">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="e1ddc-148">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="e1ddc-148">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e1ddc-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1ddc-149">See Also</span></span>  
 [<span data-ttu-id="e1ddc-150">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e1ddc-150">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="e1ddc-151">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e1ddc-151">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="e1ddc-152">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e1ddc-152">C# Keywords</span></span>](index.md)  
 <span data-ttu-id="e1ddc-153">[Yöntem parametreleri](method-parameters.md) [başvuru semantiği ile değer türleri](../../reference-semantics-with-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="e1ddc-153">[Method Parameters](method-parameters.md) [Reference Semantics with Value Types](../../reference-semantics-with-value-types.md)</span></span>
