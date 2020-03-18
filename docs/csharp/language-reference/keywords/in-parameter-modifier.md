---
title: parametre değiştirici - C# Referans
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: cbde7a571fb71ed7577077c77a5c61db553ec859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173620"
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="3b4e4-102">parametre değiştirici (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="3b4e4-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="3b4e4-103">Anahtar `in` kelime bağımsız değişkenlerin başvuruyla geçirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="3b4e4-104">Bu, resmi parametreyi bağımsız değişken için bir diğer ad yapar, bu da bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="3b4e4-105">Başka bir deyişle, parametre üzerinde herhangi bir işlem bağımsız değişken üzerinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="3b4e4-106">Bu, `in` bağımsız değişkenlerin çağrılan yöntemle değiştirilememek [dışında, ref](ref.md) veya [çıkış](out-parameter-modifier.md) anahtar kelimeleri gibidir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-106">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="3b4e4-107">Bağımsız `ref` değişkenler değiştirilebilirken, `out` bağımsız değişkenler çağrılan yöntem tarafından değiştirilmelidir ve bu değişiklikler çağrı bağlamında gözlemlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-107">Whereas `ref` arguments may be modified, `out` arguments must be modified by the called method, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="3b4e4-108">Önceki örnek, değiştiricinin `in` arama yerinde genellikle gereksiz olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-108">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="3b4e4-109">Yalnızca yöntem bildiriminde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-109">It is only required in the method declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="3b4e4-110">Anahtar `in` kelime, tür parametresinin bir `foreach` deyimin parçası olarak veya LINQ sorgusundaki bir yan tümcenin `join` parçası olarak karşıt olduğunu belirtmek için genel bir tür parametresi ile de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-110">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="3b4e4-111">Bu bağlamlarda `in` anahtar kelimenin kullanımı hakkında daha fazla bilgi için, tüm bu kullanımlara bağlantılar sağlayan içeriye bakın. [in](in.md)</span><span class="sxs-lookup"><span data-stu-id="3b4e4-111">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
<span data-ttu-id="3b4e4-112">Bağımsız değişken `in` olarak geçirilen değişkenler, bir yöntem çağrısında geçirilmeden önce başharflere geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-112">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="3b4e4-113">Ancak, çağrılan yöntem bir değer atamaz veya bağımsız değişkeni değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-113">However, the called method may not assign a value or modify the argument.</span></span>  

<span data-ttu-id="3b4e4-114">`in` Parametre değiştirici C# 7.2 ve sonraki durumlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-114">The `in` parameter modifier is available in C# 7.2 and later.</span></span> <span data-ttu-id="3b4e4-115">Önceki sürümlerde derleyici hatası `CS8107` oluşturulur ("Özellik 'yalnızca başvuru' C# 7.0'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-115">Previous versions generate compiler error `CS8107` ("Feature 'readonly references' is not available in C# 7.0.</span></span> <span data-ttu-id="3b4e4-116">Lütfen dil sürüm 7.2 veya daha büyük kullanın.") Derleyici dili sürümünü yapılandırmak için [C# dil sürümünü seçin'e](../configure-language-version.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-116">Please use language version 7.2 or greater.") To configure the compiler language version, see [Select the C# language version](../configure-language-version.md).</span></span>

<span data-ttu-id="3b4e4-117">, `in` `ref`ve `out` anahtar kelimeler aşırı yük çözümlemesi amacıyla yöntem imzasının bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-117">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="3b4e4-118">Bu nedenle, tek fark bir yöntemin bir `ref` bağımsız `in` değişken ilerlerken `out` diğerinin bir bağımsız değişken almasıysa, yöntemler aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-118">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="3b4e4-119">Örneğin, aşağıdaki kod derlenilmeyecektir:</span><span class="sxs-lookup"><span data-stu-id="3b4e4-119">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="3b4e4-120">Varlığına göre aşırı `in` yüklemeye izin verilir:</span><span class="sxs-lookup"><span data-stu-id="3b4e4-120">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="3b4e4-121">Aşırı yükleme çözünürlüğü kuralları</span><span class="sxs-lookup"><span data-stu-id="3b4e4-121">Overload resolution rules</span></span>

<span data-ttu-id="3b4e4-122">Bağımsız değişkenlerin motivasyonunu anlayarak, değerlere `in` karşılık gelen bağımsız değişkenlerle yöntemleriçin aşırı yük çözümleme kurallarını anlayabilirsiniz. `in`</span><span class="sxs-lookup"><span data-stu-id="3b4e4-122">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="3b4e4-123">Parametreleri kullanarak `in` yöntemleri tanımlamak potansiyel bir performans optimizasyonudur.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-123">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="3b4e4-124">Bazı `struct` tür bağımsız değişkenleri boyutu büyük olabilir ve yöntemleri sıkı döngüler veya kritik kod yolları çağrıldığında, bu yapıları kopyalama maliyeti önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-124">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="3b4e4-125">Çağrılan `in` yöntem bu bağımsız değişkenin durumunu değiştirmediği için bağımsız değişkenlerin güvenle başvuruyla geçirilebileceğini belirtmek için parametreleri bildiren yöntemler.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-125">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="3b4e4-126">Bu bağımsız değişkenleri referansla geçirme (potansiyel olarak) pahalı kopyayı önler.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-126">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span>

<span data-ttu-id="3b4e4-127">Arama `in` sitesindeki bağımsız değişkenler için belirtme genellikle isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-127">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="3b4e4-128">Bağımsız değişkenleri değere göre geçirmekle `in` değiştirici kullanarak referansla geçirmek arasında anlamsal bir fark yoktur.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-128">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="3b4e4-129">Bağımsız `in` değişkenin değerinin değiştirilebileceğini belirtmeniz gerekmedığından, arama sitesindeki değiştirici isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-129">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="3b4e4-130">Bağımsız değişkenin `in` değere göre değil, referans la geçtiğinden emin olmak için çağrı yerindeki değiştiriciyi açıkça eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-130">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="3b4e4-131">Açıkça kullanarak `in` aşağıdaki iki etkisi vardır:</span><span class="sxs-lookup"><span data-stu-id="3b4e4-131">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="3b4e4-132">İlk olarak, `in` çağrı yerinde belirtilmesi derleyiciyi eşleşen `in` bir parametre ile tanımlanan bir yöntem seçmeye zorlar.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-132">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="3b4e4-133">Aksi takdirde, iki yöntem sadece `in`varlığında farklı olduğunda , değer aşırı yük daha iyi bir maç.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-133">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="3b4e4-134">İkinci olarak, `in` belirtme, bir bağımsız değişkeni başvuruyla geçirme niyetinizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-134">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="3b4e4-135">Kullanılan bağımsız `in` değişken, doğrudan başvurulabilen bir konumu temsil etmelidir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-135">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="3b4e4-136">Aynı genel kurallar `out` `ref` ve bağımsız değişkenler geçerlidir: Değerleri üreten sabitleri, sıradan özellikleri veya diğer ifadeleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-136">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="3b4e4-137">Aksi takdirde, `in` çağrı yerinde atlayarak, derleyiciye yönteme salt okunur başvuruyla geçmek için geçici bir değişken oluşturmasına izin vereceğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-137">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="3b4e4-138">Derleyici bağımsız değişkenlerle `in` çeşitli kısıtlamaları aşmak için geçici bir değişken oluşturur:</span><span class="sxs-lookup"><span data-stu-id="3b4e4-138">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="3b4e4-139">Geçici bir değişken, zaman sabitlerinin `in` parametre olarak derlenmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-139">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="3b4e4-140">Geçici bir değişken, parametreler için `in` özellikler veya diğer ifadelere izin verir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-140">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="3b4e4-141">Geçici bir değişken, bağımsız değişken türünden parametre türüne örtülü dönüştürme nin olduğu bağımsız değişkenlere izin verir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-141">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="3b4e4-142">Önceki tüm örneklerde derleyici, sabitin, özelliğin veya diğer ifadenin değerini depolayan geçici bir değişken oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-142">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="3b4e4-143">Aşağıdaki kod şu kuralları göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="3b4e4-143">The following code illustrates these rules:</span></span>

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

<span data-ttu-id="3b4e4-144">Şimdi, değer bağımsız değişkenleri tarafından kullanılan başka bir yöntem kullanılabilir olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-144">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="3b4e4-145">Sonuçlar aşağıdaki kodda gösterildiği gibi değişir:</span><span class="sxs-lookup"><span data-stu-id="3b4e4-145">The results change as shown in the following code:</span></span>

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

<span data-ttu-id="3b4e4-146">Bağımsız değişkenin başvuru yla geçtiği tek yöntem çağrısı son yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-146">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="3b4e4-147">Önceki kod basitlik için bağımsız değişken türü olarak kullanır. `int`</span><span class="sxs-lookup"><span data-stu-id="3b4e4-147">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="3b4e4-148">Çoğu `int` modern makinelerde bir referans daha büyük olduğundan, tek bir `int` okuma referans olarak geçen hiçbir yararı yoktur.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-148">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span>

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="3b4e4-149">Parametrelerüzerindeki `in` sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="3b4e4-149">Limitations on `in` parameters</span></span>

<span data-ttu-id="3b4e4-150">Aşağıdaki yöntem türleri `in`için `ref`, `out` ve anahtar kelimeleri kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="3b4e4-150">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="3b4e4-151">Async değiştirici kullanarak tanımladığınız [async](async.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-151">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="3b4e4-152">[Verim getirisi](yield.md) veya `yield break` deyimi içeren yineleyici yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-152">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="3b4e4-153">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="3b4e4-153">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3b4e4-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b4e4-154">See also</span></span>

- [<span data-ttu-id="3b4e4-155">C# Referans</span><span class="sxs-lookup"><span data-stu-id="3b4e4-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3b4e4-156">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3b4e4-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3b4e4-157">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="3b4e4-157">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3b4e4-158">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="3b4e4-158">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="3b4e4-159">Güvenli verimli kod yazın</span><span class="sxs-lookup"><span data-stu-id="3b4e4-159">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
