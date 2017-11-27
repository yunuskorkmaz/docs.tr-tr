---
title: "Ölçü Birimleri (F#)"
description: "Nasıl kayan nokta öğrenin ve F # imzalı tamsayı değerleri, genellikle uzunluğu, ses ve yığın belirtmek için kullanılan ölçü ilişkili."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: cb2eb658-df6c-422e-afad-97422609c773
ms.openlocfilehash: 2d0683e864c5684a78c02e177c296d3067295723
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="units-of-measure"></a><span data-ttu-id="20e38-104">Ölçü Birimleri</span><span class="sxs-lookup"><span data-stu-id="20e38-104">Units of Measure</span></span>

<span data-ttu-id="20e38-105">Kayan nokta ve imzalı tamsayı değerleri F # genellikle toplu vb. uzunluğu, birim, belirtmek için kullanılan ölçü ilişkili sahip.</span><span class="sxs-lookup"><span data-stu-id="20e38-105">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="20e38-106">Birimleriyle miktarları kullanarak önlemeye yardımcı olan aritmetik ilişkileri doğru birimleri olduğunu doğrulamak derleyici etkinleştirmek programlama hatalarını.</span><span class="sxs-lookup"><span data-stu-id="20e38-106">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>


## <a name="syntax"></a><span data-ttu-id="20e38-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20e38-107">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="20e38-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20e38-108">Remarks</span></span>
<span data-ttu-id="20e38-109">Önceki sözdizimi tanımlar *birim adı* bir ölçü olarak.</span><span class="sxs-lookup"><span data-stu-id="20e38-109">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="20e38-110">İsteğe bağlı bölümü önceden tanımlanmış birimleri açısından yeni bir ölçü tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20e38-110">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="20e38-111">Örneğin, aşağıdaki satırı ölçü tanımlar `cm` (santimetre).</span><span class="sxs-lookup"><span data-stu-id="20e38-111">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="20e38-112">Aşağıdaki satırı ölçü tanımlar `ml` (milliliter) bir Santimetreküp olarak (`cm^3`).</span><span class="sxs-lookup"><span data-stu-id="20e38-112">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="20e38-113">Önceki sözdiziminde *ölçü* birimleri içerir formülüdür.</span><span class="sxs-lookup"><span data-stu-id="20e38-113">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="20e38-114">Formüllerde birimleri içeren, tam sayı powers (pozitif ve negatif) desteklenir, birimleri arasında boşluk gösterir iki birimleri, bir ürün `*` de birimleri, bir ürün gösterir ve `/` birimlerin bir sayının gösterir.</span><span class="sxs-lookup"><span data-stu-id="20e38-114">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="20e38-115">Karşılıklı bir birim için negatif tamsayı güç ya da kullanabilirsiniz veya `/` pay ve bir birim formülün payda arasında ayrım gösterir.</span><span class="sxs-lookup"><span data-stu-id="20e38-115">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="20e38-116">Payda birden çok birim ayraç içinde kullanılması.</span><span class="sxs-lookup"><span data-stu-id="20e38-116">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="20e38-117">Birimleri ayrılmış sonra boşluklarla bir `/` payda, ancak aşağıdaki birimleri parçası olacak şekilde yorumlanır bir `*` pay parçası olacak şekilde yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="20e38-117">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="20e38-118">1 ya da tek başına dimensionless bir miktar belirtmek için birim ifadelerde veya diğer birimler, pay olduğu gibi birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20e38-118">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="20e38-119">Örneğin, bir hızı birimi olarak yazılacak `1/s`, burada `s` saniye gösterir.</span><span class="sxs-lookup"><span data-stu-id="20e38-119">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="20e38-120">Parantez birim formüller kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="20e38-120">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="20e38-121">Birim formüllerde sayısal dönüşüm sabitleri belirtmeyin; Ancak, dönüştürme sabitleri birimleriyle ayrı olarak tanımlamak ve birim işaretli hesaplamalarında kullanın.</span><span class="sxs-lookup"><span data-stu-id="20e38-121">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="20e38-122">Aynı anlamda birim formüller eşdeğer çeşitli şekillerde yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="20e38-122">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="20e38-123">Bu nedenle, derleyici, negatif katlarını reciprocals, grupları birimleri için tek bir pay ve bir paydası dönüştürür ve pay ve payda birimlerinde alfabetik olarak sıralar tutarlı bir form birim formüller dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="20e38-123">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="20e38-124">Örneğin, birim formüller `kg m s^-2` ve `m /s s * kg` her ikisi de dönüştürülür `kg m/s^2`.</span><span class="sxs-lookup"><span data-stu-id="20e38-124">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="20e38-125">Kayan nokta ifadelerinde ölçü kullanın.</span><span class="sxs-lookup"><span data-stu-id="20e38-125">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="20e38-126">Ölçü kayan nokta sayıları ilişkili birimler birlikte kullanarak başka bir tür güvenliği düzeyi ekler ve yardımcı formüller zayıf yazılmış kayan noktalı sayının kullandığınızda oluşabilecek birim uyuşmazlığı hataları kaçının.</span><span class="sxs-lookup"><span data-stu-id="20e38-126">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="20e38-127">Bir kayan yazarsanız, birimleri kullanan noktası ifade ifade birimlerinde eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="20e38-127">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="20e38-128">Aşağıdaki örneklerde gösterildiği gibi köşeli, birim formülde ile değişmez değerleri açıklama ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20e38-128">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="20e38-129">Sayı ve açılı ayraç arasında bir boşluk koymayın; Ancak, değişmez değer soneki gibi içerebilir `f`, aşağıdaki örnekte olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="20e38-129">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="20e38-130">Böyle bir ek açıklama değişmez değeri türünü ilkel türünden değiştirir (gibi `float`) dimensioned türü gibi `float<cm>` veya bu durumda, `float<miles/hour>`.</span><span class="sxs-lookup"><span data-stu-id="20e38-130">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="20e38-131">Bir birim bir ek açıklamanın `<1>` dimensionless bir miktar ve türünü ilkel tür bir birim parametresi olmadan eşdeğer olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="20e38-131">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="20e38-132">Bir ölçü türü bir kayan nokta veya köşeli gösterilen ek birim açıklamanın birlikte tam sayı türdür.</span><span class="sxs-lookup"><span data-stu-id="20e38-132">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="20e38-133">Bu nedenle, ne zaman yazdığınız dönüştürme türü `g` (gram) için `kg` (kilogram), aşağıdaki gibi türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20e38-133">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="20e38-134">Ölçü için derleme zamanı birimi denetimi kullanılır ancak çalışma zamanı ortamında kalıcı değildir.</span><span class="sxs-lookup"><span data-stu-id="20e38-134">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="20e38-135">Bu nedenle, performans etkilemez.</span><span class="sxs-lookup"><span data-stu-id="20e38-135">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="20e38-136">Ölçü birimleri yalnızca kayan nokta türleri, herhangi bir türüne uygulanabilir; Ancak, tek kayan nokta türleri, tam sayı türleri ve ondalık türleri dimensioned destek miktarları imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="20e38-136">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="20e38-137">Bu nedenle, yalnızca ilkel türler ve bu ilkel türler içeren toplamalar ölçü kullanılacak mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="20e38-137">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="20e38-138">Aşağıdaki örnek ölçü kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="20e38-138">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]
    
<span data-ttu-id="20e38-139">Aşağıdaki kod örneğinde dimensionless kayan nokta sayısı dimensioned bir kayan noktalı değeri dönüştürme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="20e38-139">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="20e38-140">Yalnızca tarafından 1.0, 1.0 boyutları uygulama çarpın.</span><span class="sxs-lookup"><span data-stu-id="20e38-140">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="20e38-141">Bu gibi bir işlevine soyut `degreesFahrenheit`.</span><span class="sxs-lookup"><span data-stu-id="20e38-141">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="20e38-142">Ayrıca, dimensionless kayan noktalı sayının beklediğiniz işlevleri dimensioned değerlerini geçirdiğinizde, birimleri iptal etmeli veya için cast `float` kullanarak `float` işleci.</span><span class="sxs-lookup"><span data-stu-id="20e38-142">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="20e38-143">Bu örnekte, bölün `1.0<degC>` bağımsız değişkenleri için `printf` çünkü `printf` dimensionless miktarları bekliyor.</span><span class="sxs-lookup"><span data-stu-id="20e38-143">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="20e38-144">Aşağıdaki örnek oturumunda bu kodu girişleri ve çıkışları gelen gösterir.</span><span class="sxs-lookup"><span data-stu-id="20e38-144">The following example session shows the outputs from and inputs to this code.</span></span>

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="20e38-145">Genel birimlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="20e38-145">Using Generic Units</span></span>
<span data-ttu-id="20e38-146">İlişkili bir ölçü olan veriler üzerinde çalışan genel işlevler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20e38-146">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="20e38-147">Tür parametresi bir tür genel bir birim birlikte belirterek aşağıdaki kod örneğinde gösterildiği gibi bunu.</span><span class="sxs-lookup"><span data-stu-id="20e38-147">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]
    
## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="20e38-148">Genel birimleriyle toplama türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="20e38-148">Creating Aggregate Types with Generic Units</span></span>
<span data-ttu-id="20e38-149">Aşağıdaki kod genel birimleri olan tek tek kayan nokta değerlerine oluşan bir toplama türü oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="20e38-149">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="20e38-150">Bu birimleri çeşitli çalışan oluşturulması tek bir türü sağlar.</span><span class="sxs-lookup"><span data-stu-id="20e38-150">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="20e38-151">Ayrıca, bir grup birimlerinin genel bir tür aynı genel tür birimleri farklı bir dizi farklı bir tür olduğu sağlayarak tür güvenliği genel birimleri korur.</span><span class="sxs-lookup"><span data-stu-id="20e38-151">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="20e38-152">Bu teknik temelini `Measure` özniteliği için tür parametre uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="20e38-152">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]
    
## <a name="units-at-runtime"></a><span data-ttu-id="20e38-153">Çalışma zamanında birimleri</span><span class="sxs-lookup"><span data-stu-id="20e38-153">Units at Runtime</span></span>
<span data-ttu-id="20e38-154">Ölçü birimleri statik türü denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20e38-154">Units of measure are used for static type checking.</span></span> <span data-ttu-id="20e38-155">Kayan nokta değerlerine derlendiğinde çalışma zamanında birimleri kayıp; bu nedenle ölçü, ortadan kalkar.</span><span class="sxs-lookup"><span data-stu-id="20e38-155">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="20e38-156">Bu nedenle, çalışma zamanında birimleri denetimini bağlıdır işlevselliği uygulamak için her türlü girişim mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="20e38-156">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="20e38-157">Örneğin, uygulama bir `ToString` birimleri yazdırmak için işlevi mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="20e38-157">For example, implementing a `ToString` function to print out the units is not possible.</span></span>


## <a name="conversions"></a><span data-ttu-id="20e38-158">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="20e38-158">Conversions</span></span>
<span data-ttu-id="20e38-159">Birimleri olan bir türü dönüştürmek için (örneğin, `float<'u>`) birimleri sahip olmayan bir türe standart dönüştürme işlevini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20e38-159">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="20e38-160">Örneğin, kullanabileceğiniz `float` dönüştürmek için bir `float` birimleri, aşağıdaki kodda gösterildiği gibi yok değeri.</span><span class="sxs-lookup"><span data-stu-id="20e38-160">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="20e38-161">Bir unitless değeri birimleri olan değerine dönüştürmek için uygun birimleriyle açıklama 1 veya 1.0 değeri tarafından çarpabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20e38-161">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="20e38-162">Ancak, birlikte çalışabilirlik Katmanlar yazmak için de bazı explicit unitless değerleri birimleriyle değerlerine dönüştürmek için kullanabileceğiniz işlev vardır.</span><span class="sxs-lookup"><span data-stu-id="20e38-162">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="20e38-163">İçinde bunlar [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modülü.</span><span class="sxs-lookup"><span data-stu-id="20e38-163">These are in the [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module.</span></span> <span data-ttu-id="20e38-164">Örneğin, bir unitless dönüştürmek için `float` için bir `float<cm>`, kullanın [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9)aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="20e38-164">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]
    
## <a name="units-of-measure-in-the-f-power-pack"></a><span data-ttu-id="20e38-165">F # güç paketindeki ölçü birimleri</span><span class="sxs-lookup"><span data-stu-id="20e38-165">Units of Measure in the F# Power Pack</span></span>
<span data-ttu-id="20e38-166">F # PowerPack'ten kullanılabilir bir birim kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="20e38-166">A unit library is available in the F# PowerPack.</span></span> <span data-ttu-id="20e38-167">Birim kitaplığı sı birimleri ve fiziksel sabitleri içerir.</span><span class="sxs-lookup"><span data-stu-id="20e38-167">The unit library includes SI units and physical constants.</span></span>


## <a name="see-also"></a><span data-ttu-id="20e38-168">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20e38-168">See Also</span></span>
[<span data-ttu-id="20e38-169">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="20e38-169">F# Language Reference</span></span>](index.md)
