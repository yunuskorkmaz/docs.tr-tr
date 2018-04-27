---
title: İptali - C# Kılavuzu
description: C# ' ın atanmamış iptali, discardable değişkenleri ve iptali kullanılabilir yöntemleri için destek açıklanır.
keywords: .NET, .NET core
author: rpetrusha
ms.author: ronpet
ms.date: 07/21/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 94badd78485ee4d3928b170d81a80743bf84102f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="discards---c-guide"></a><span data-ttu-id="3a484-104">İptali - C# Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3a484-104">Discards - C# Guide</span></span>

<span data-ttu-id="3a484-105">C# 7. 0'dan başlayarak, C# destekler atar, uygulama kodunda kasıtlı olarak kullanılmayan geçici, sahte değişkenleri olduğu.</span><span class="sxs-lookup"><span data-stu-id="3a484-105">Starting with C# 7.0, C# supports discards, which are temporary, dummy variables that are intentionally unused in application code.</span></span> <span data-ttu-id="3a484-106">İptali atanmamış değişkenlere eşdeğer; bir değere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="3a484-106">Discards are equivalent to unassigned variables; they do not have a value.</span></span> <span data-ttu-id="3a484-107">Yalnızca bir tek atma değişken yoktur ve bu değişken depolama bile ayrılan değil çünkü iptali bellek ayırmaları azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="3a484-107">Because there is only a single discard variable, and that variable may not even be allocated storage, discards can reduce memory allocations.</span></span> <span data-ttu-id="3a484-108">Kodunuzu Temizle amacı olun çünkü bunlar okunabilirlik ve bakımı geliştirin.</span><span class="sxs-lookup"><span data-stu-id="3a484-108">Because they make the intent of your code clear, they enhance its readability and maintainability.</span></span>

<span data-ttu-id="3a484-109">Alt çizgi atayarak bir değişken bir atma olduğunu gösteriyor (`_`) ad olarak.</span><span class="sxs-lookup"><span data-stu-id="3a484-109">You indicate that a variable is a discard by assigning it the underscore (`_`) as its name.</span></span> <span data-ttu-id="3a484-110">Örneğin, aşağıdaki yöntem çağrısı birinci ve ikinci değer iptali olacak 3-tanımlama grubu döndürür ve *alanı* tarafından döndürülen ilgili üçüncü bileşen olarak daha önce bildirilen değişkenidir  *GetCityInformation*:</span><span class="sxs-lookup"><span data-stu-id="3a484-110">For example, the following method call returns a 3-tuple in which the first and second values are discards and *area* is a previously declared variable to be set to the corresponding third component returned by *GetCityInformation*:</span></span>

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

<span data-ttu-id="3a484-111">C# 7. 0'iptali aşağıdaki bağlamlarında atamaları desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3a484-111">In C# 7.0, discards are supported in assignments in the following contexts:</span></span>

- <span data-ttu-id="3a484-112">Dizi ve nesne [deconstruction](deconstruct.md).</span><span class="sxs-lookup"><span data-stu-id="3a484-112">Tuple and object [deconstruction](deconstruct.md).</span></span>
- <span data-ttu-id="3a484-113">İle desen eşleştirme [olan](language-reference/keywords/is.md) ve [geçiş](language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="3a484-113">Pattern matching with [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md).</span></span>
- <span data-ttu-id="3a484-114">Yöntemleriyle çağrıları `out` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="3a484-114">Calls to methods with `out` parameters.</span></span>
- <span data-ttu-id="3a484-115">Tek başına `_` durumlarda `_` kapsamında değil.</span><span class="sxs-lookup"><span data-stu-id="3a484-115">A standalone `_` when no `_` is in scope.</span></span>

<span data-ttu-id="3a484-116">Zaman `_` olan değerini veya atama işleminde ürettiği derleyici hatası CS0301, kullanım almaya geçerli bir at "adı '\_' geçerli bağlamda mevcut değil".</span><span class="sxs-lookup"><span data-stu-id="3a484-116">When `_` is a valid discard, attempting to retrieve its value or use it in an assignment operation generates compiler error CS0301, "The name '\_' does not exist in the current context".</span></span> <span data-ttu-id="3a484-117">Bunun nedeni, `_` bir değer atanmadı ve bir depolama konumu bile atanmış olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3a484-117">This is because `_` is not assigned a value, and may not even be assigned a storage location.</span></span> <span data-ttu-id="3a484-118">Gerçek bir değişken olsaydı, önceki örnekte olduğu gibi birden fazla değer atmak değil.</span><span class="sxs-lookup"><span data-stu-id="3a484-118">If it were an actual variable, you could not discard more than one value, as the previous example did.</span></span>

## <a name="tuple-and-object-deconstruction"></a><span data-ttu-id="3a484-119">Dizi ve nesne deconstruction</span><span class="sxs-lookup"><span data-stu-id="3a484-119">Tuple and object deconstruction</span></span>

<span data-ttu-id="3a484-120">İptali uygulama kodunuz bazı başlığın öğeleri kullanır ancak başkalarının yoksayar içeren başlık çalışma özellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="3a484-120">Discards are particularly useful in working with tuples when your application code uses some tuple elements but ignores others.</span></span> <span data-ttu-id="3a484-121">Örneğin, aşağıdaki `QueryCityDataForYears` yöntemi bir şehir, kendi alanı, bir yılın, o yıl, ikinci bir yıl ve bu ikinci yıl Şehir 's popülasyon Şehir 's popülasyon adıyla 6-tanımlama grubu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a484-121">For example, the following `QueryCityDataForYears` method returns a 6-tuple with the name of a city, its area, a year, the city's population for that year, a second year, and the city's population for that second year.</span></span> <span data-ttu-id="3a484-122">Örnek popülasyondaki bu iki yıl arasında değişiklik gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a484-122">The example shows the change in population between those two years.</span></span> <span data-ttu-id="3a484-123">Verileri tanımlama grubu bulunan, biz Şehir alanıyla unconcerned ve şehir adı ve tasarım zamanında iki tarih biliyoruz.</span><span class="sxs-lookup"><span data-stu-id="3a484-123">Of the data available from the tuple, we're unconcerned with the city area, and we know the city name and the two dates at design-time.</span></span> <span data-ttu-id="3a484-124">Sonuç olarak, biz yalnızca düzeninde depolanan iki popülasyon değerleri ilgileniyor ve onun kalan değerler iptali olarak işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3a484-124">As a result, we're only interested in the two population values stored in the tuple, and can handle its remaining values as discards.</span></span>  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

<span data-ttu-id="3a484-125">İptali içeren başlık deconstructing daha fazla bilgi için bkz: [tanımlama grupları ve diğer türleri Deconstructing](deconstruct.md#deconstructing-tuple-elements-with-discards).</span><span class="sxs-lookup"><span data-stu-id="3a484-125">For more information on deconstructing tuples with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-tuple-elements-with-discards).</span></span>

<span data-ttu-id="3a484-126">`Deconstruct` Sınıf, yapı veya arabirim yöntemini de alabilir ve verileri bir nesneden belirli bir dizi deconstruct olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3a484-126">The `Deconstruct` method of a class, structure, or interface also allows you to retrieve and deconstruct a specific set of data from an object.</span></span> <span data-ttu-id="3a484-127">Yalnızca bir alt kümesini deconstructed değerleri ile çalışma ilgilendiğiniz zaman iptali kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a484-127">You can use discards when you are interested in working with only a subset of the deconstructed values.</span></span> <span data-ttu-id="3a484-128">Aşağıdaki örnek deconstructs Ihe bir `Person` dört dizeleri (ilk ve son adları, şehir ve durumu) nesnesine ancak son adı ve durum atar.</span><span class="sxs-lookup"><span data-stu-id="3a484-128">Ihe following example deconstructs a `Person` object into four strings (the first and last names, the city, and the state), but discards the last name and the state.</span></span>

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

<span data-ttu-id="3a484-129">Kullanıcı tanımlı türler iptali ile deconstructing daha fazla bilgi için bkz: [tanımlama grupları ve diğer türleri Deconstructing](deconstruct.md#deconstructing-a-user-defined-type-with-discards).</span><span class="sxs-lookup"><span data-stu-id="3a484-129">For more information on deconstructing user-defined types with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-a-user-defined-type-with-discards).</span></span>

## <a name="pattern-matching-with-switch-and-is"></a><span data-ttu-id="3a484-130">Deseni ile eşleşen `switch` ve `is`</span><span class="sxs-lookup"><span data-stu-id="3a484-130">Pattern matching with `switch` and `is`</span></span>

<span data-ttu-id="3a484-131">*Düzeni atmak* deseni ile eşleşen kullanılabilir [olan](language-reference/keywords/is.md) ve [geçiş](language-reference/keywords/switch.md) anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="3a484-131">The *discard pattern* can be used in pattern matching with the [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md) keywords.</span></span> <span data-ttu-id="3a484-132">Her ifadesi her zaman atma eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="3a484-132">Every expression always matches the discard pattern.</span></span>

<span data-ttu-id="3a484-133">Aşağıdaki örnek tanımlayan bir `ProvidesFormatInfo` kullanan yöntemi [olan](language-reference/keywords/is.md) nesneyi sağlayıp sağlamadığını belirlemek için deyimleri bir <xref:System.IFormatProvider> uygulama ve testleri nesne olup `null`.</span><span class="sxs-lookup"><span data-stu-id="3a484-133">The following example defines a `ProvidesFormatInfo` method that uses [is](language-reference/keywords/is.md) statements to determine whether an object provides an <xref:System.IFormatProvider> implementation and tests whether the object is `null`.</span></span> <span data-ttu-id="3a484-134">Ayrıca herhangi bir tür null olmayan nesneleri işlemek için atma desen kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a484-134">It also uses the discard pattern to handle non-null objects of any other type.</span></span>

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a><span data-ttu-id="3a484-135">Out Parametreleri yöntemleriyle çağrıları</span><span class="sxs-lookup"><span data-stu-id="3a484-135">Calls to methods with out parameters</span></span>

<span data-ttu-id="3a484-136">Çağrılırken `Deconstruct` atmak değerlerini tek tek bir kullanıcı tanımlı tür (örneği sınıf, yapı veya arabirim), deconstruct yöntemi `out` bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="3a484-136">When calling the `Deconstruct` method to deconstruct a user-defined type (an instance of a class, structure, or interface), you can discard the values of individual `out` arguments.</span></span> <span data-ttu-id="3a484-137">Ancak değerini de atabilirsiniz `out` out parametresi ile herhangi bir yöntemini çağırmadan zaman bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="3a484-137">But you can also discard the value of `out` arguments when calling any method with an out parameter.</span></span> 

<span data-ttu-id="3a484-138">Aşağıdaki örnek çağrıları [DateTime.TryParse (dize, DateTime çıkışı)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) bir tarih dize gösterimini geçerli kültürün geçerli olup olmadığını belirlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="3a484-138">The following example calls the [DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) method to determine whether the string representation of a date is valid in the current culture.</span></span> <span data-ttu-id="3a484-139">Örneğin yalnızca tarih dizesi doğrulama ile tarih ayıklamak için ayrıştırma değil kaygı çünkü `out` olmayan bir atma yöntemi için bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="3a484-139">Because the example is concerned only with validating the date string and not with parsing it to extract the date, the `out` argument to the method is a discard.</span></span>

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a><span data-ttu-id="3a484-140">Tek başına atma</span><span class="sxs-lookup"><span data-stu-id="3a484-140">A standalone discard</span></span>

<span data-ttu-id="3a484-141">Tek başına atma yoksaymak için seçtiğiniz herhangi bir değişken belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a484-141">You can use a standalone discard to indicate any variable that you choose to ignore.</span></span> <span data-ttu-id="3a484-142">Aşağıdaki örnek bir tek başına atma gözardı eder <xref:System.Threading.Tasks.Task> zaman uyumsuz bir işlem tarafından döndürülen nesne.</span><span class="sxs-lookup"><span data-stu-id="3a484-142">The following example uses a standalone discard to ignore the <xref:System.Threading.Tasks.Task> object returned by an asynchronous operation.</span></span> <span data-ttu-id="3a484-143">Bu, yaklaşık tamamlamak için olduğu gibi işlemi oluşturur özel durum gizleme etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="3a484-143">This has the effect of suppressing the exception that the operation throws as it is about to complete.</span></span>

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

<span data-ttu-id="3a484-144">Unutmayın `_` da geçerli bir tanımlayıcı değil.</span><span class="sxs-lookup"><span data-stu-id="3a484-144">Note that `_` is also a valid identifier.</span></span> <span data-ttu-id="3a484-145">Desteklenen bir bağlam dışında kullanıldığında `_` bir atma olarak değil, ancak geçerli bir değişken olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3a484-145">When used outside of a supported context, `_` is treated not as a discard but as a valid variable.</span></span> <span data-ttu-id="3a484-146">Tanımlayıcı adlı `_` kullanımını kapsamda zaten `_` atma tek başına olarak neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="3a484-146">If an identifier named `_` is already in scope, the use of `_` as a standalone discard can result in:</span></span>

- <span data-ttu-id="3a484-147">Kapsam içinde değerini yanlışlıkla değiştirilmesini `_` hedeflenen atma değerini atayarak değişken.</span><span class="sxs-lookup"><span data-stu-id="3a484-147">Accidental modification of the value of the in-scope `_` variable by assigning it the value of the intended discard.</span></span> <span data-ttu-id="3a484-148">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3a484-148">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]
 
- <span data-ttu-id="3a484-149">Tür güvenliği ihlal eden bir derleyici hatası.</span><span class="sxs-lookup"><span data-stu-id="3a484-149">A compiler error for violating type safety.</span></span> <span data-ttu-id="3a484-150">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3a484-150">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]
 
- <span data-ttu-id="3a484-151">Derleyici Hatası CS0136, "Bu adı kapsayan bir yerel kapsamında bir yerel veya parametre tanımlamak için kullanılır çünkü bir yerel veya '_' adlı parametre bu kapsamda bildirilemez."</span><span class="sxs-lookup"><span data-stu-id="3a484-151">Compiler error CS0136, "A local or parameter named '_' cannot be declared in this scope because that name is used in an enclosing local scope to define a local or parameter."</span></span> <span data-ttu-id="3a484-152">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3a484-152">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a><span data-ttu-id="3a484-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a484-153">See also</span></span>
<span data-ttu-id="3a484-154">[Tanımlama grupları ve diğer türleri deconstructing](deconstruct.md) </span><span class="sxs-lookup"><span data-stu-id="3a484-154">[Deconstructing tuples and other types](deconstruct.md) </span></span>  
<span data-ttu-id="3a484-155">[`is` Anahtar sözcüğü](language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="3a484-155">[`is` keyword](language-reference/keywords/is.md) </span></span>  
[<span data-ttu-id="3a484-156">`switch` Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="3a484-156">`switch` keyword</span></span>](language-reference/keywords/switch.md)   
