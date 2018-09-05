---
title: Ölçü Birimleri (F#)
description: 'Nasıl kayan nokta öğrenin ve F # imzalı tamsayı değerleri, genellikle uzunluğu, ses ve yığın belirtmek için kullanılan ölçü birimlerini ilişkili.'
ms.date: 05/16/2016
ms.openlocfilehash: 6075742ec80d9510be51d4565e3397931c9f68c7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517432"
---
# <a name="units-of-measure"></a><span data-ttu-id="d8e30-103">Ölçü Birimleri</span><span class="sxs-lookup"><span data-stu-id="d8e30-103">Units of Measure</span></span>

<span data-ttu-id="d8e30-104">Kayan nokta ve imzalı tamsayı değerleri F # genellikle toplu vb. uzunluğu, birim belirtmek için kullanılan ölçü birimlerini ilişkili.</span><span class="sxs-lookup"><span data-stu-id="d8e30-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="d8e30-105">Birimleri ile miktarlar kullanarak önlemeye yardımcı olur aritmetik ilişkileri doğru birimleri, yüklü olduğunu doğrulamak derleyiciyi etkinleştir programlama hatalarını.</span><span class="sxs-lookup"><span data-stu-id="d8e30-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>


## <a name="syntax"></a><span data-ttu-id="d8e30-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8e30-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="d8e30-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8e30-107">Remarks</span></span>
<span data-ttu-id="d8e30-108">Önceki söz dizimi *birim adı* ölçü birimi olarak.</span><span class="sxs-lookup"><span data-stu-id="d8e30-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="d8e30-109">İsteğe bağlı bir parçası, önceden tanımlanmış birimleri yeni bir ölçü tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8e30-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="d8e30-110">Örneğin, aşağıdaki satırı ölçü tanımlar `cm` (santimetre).</span><span class="sxs-lookup"><span data-stu-id="d8e30-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="d8e30-111">Aşağıdaki satırı ölçü tanımlar `ml` (milliliter) üçüncü dereceden santimetre olarak (`cm^3`).</span><span class="sxs-lookup"><span data-stu-id="d8e30-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="d8e30-112">Önceki sözdiziminde, *ölçü* birim içeren bir formül.</span><span class="sxs-lookup"><span data-stu-id="d8e30-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="d8e30-113">Birim içeren formüllerde, tam sayı katlarını (pozitif ve negatif) desteklenir; birimleri arasında boşluk iki birimleri, bir ürünü belirtmek `*` de birimleri, bir ürün gösterir ve `/` birimlerinin bir bölümü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8e30-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="d8e30-114">Karşılıklı bir birim için bir negatif tam sayı üssü ya da kullanabilirsiniz veya `/` payı ve bir birim formülün paydayı arasında bir ayrım gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8e30-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="d8e30-115">Payda içinde birden çok birimi parantez içine alınır.</span><span class="sxs-lookup"><span data-stu-id="d8e30-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="d8e30-116">Sonraki boşluklar ayrılmış birim bir `/` payda, ancak izleyen tüm birimleri bir parçası olacak şekilde yorumlanır bir `*` pay parçası olacak şekilde yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="d8e30-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="d8e30-117">1 birim ifadelerde ya da tek başına bir dimensionless miktar belirtmek için veya diğer birimleri, gibi pay birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8e30-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="d8e30-118">Örneğin, bir oran için birim olarak yazılacak `1/s`burada `s` saniye gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8e30-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="d8e30-119">Parantez birim formüllerde kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="d8e30-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="d8e30-120">Birim formüllerde sayısal dönüştürme sabitleri belirtmeyin; Ancak, dönüşümü sabitleri birimleri ile ayrı olarak tanımlayın ve bunları birim işaretli hesaplamalar kullanın.</span><span class="sxs-lookup"><span data-stu-id="d8e30-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="d8e30-121">Aynı anlamda birim formülleri eşdeğer çeşitli şekillerde yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8e30-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="d8e30-122">Bu nedenle, derleyici negatif powers reciprocals, grupları birimleri için tek bir pay ve bir paydası dönüştürür ve birimleri pay ve paydası alfabetik olarak sıralar tutarlı bir form birim formülleri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d8e30-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="d8e30-123">Örneğin, birim formülleri `kg m s^-2` ve `m /s s * kg` hem dönüştürülür `kg m/s^2`.</span><span class="sxs-lookup"><span data-stu-id="d8e30-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="d8e30-124">Kayan nokta ifadeleri ölçü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d8e30-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="d8e30-125">Ölçü kayan noktalı sayıları ilişkili birimleri ile birlikte kullanarak başka bir tür güvenliği düzeyini ekler ve yardımcı formüllerde zayıf yazılmış kayan noktalı sayıları kullanırken oluşabilecek birim uyuşmazlığı hataları önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8e30-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="d8e30-126">Kayan yazarsanız birimleri kullanan noktası ifadesi ifade birimleriyle aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8e30-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="d8e30-127">Aşağıdaki örneklerde gösterildiği gibi bir birim formül köşeli parantez içinde sabit değerleri açıklama ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8e30-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="d8e30-128">Açılı ayraç arasındaki boşluk koymayın; Ancak, değişmez değer soneki gibi içerebilir `f`, aşağıdaki örnekte olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="d8e30-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="d8e30-129">Böyle bir ek açıklama değişmez değer türü kendi temel türünden değiştirir (gibi `float`) dimensioned bir türe gibi `float<cm>` veya bu durumda, `float<miles/hour>`.</span><span class="sxs-lookup"><span data-stu-id="d8e30-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="d8e30-130">Bir birim ek açıklamanın `<1>` dimensionless miktarını ve türünü ilkel tür bir birim parametresi olmadan eşdeğer olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8e30-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="d8e30-131">Ölçü türü bir kayan nokta veya imzalı tamsayı türü köşeli ayraç içinde gösterilen birim ek açıklamanın birlikte.</span><span class="sxs-lookup"><span data-stu-id="d8e30-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="d8e30-132">Bu nedenle, bir dönüştürme türü yazdığınızda `g` (gram) için `kg` (kilogram) aşağıdaki gibi türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8e30-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="d8e30-133">Ölçü birimleri için derleme zamanı birimi denetimi kullanılır ancak çalışma zamanı ortamında kalıcı değildir.</span><span class="sxs-lookup"><span data-stu-id="d8e30-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="d8e30-134">Bu nedenle, performans etkilemez.</span><span class="sxs-lookup"><span data-stu-id="d8e30-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="d8e30-135">Ölçü birimleri, yalnızca kayan nokta tür herhangi bir tür uygulanabilir; Ancak, yalnızca kayan nokta türleri, tam sayı türleri ve ondalık türleri dimensioned destek miktarlar imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="d8e30-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="d8e30-136">Bu nedenle, yalnızca temel eleman türleri ve bu ilkel türler içeren toplamaları ölçü kullanılacak mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="d8e30-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="d8e30-137">Aşağıdaki örnek, ölçü kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8e30-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]
    
<span data-ttu-id="d8e30-138">Aşağıdaki kod örneği, dimensionless kayan noktası numarasından dimensioned kayan nokta değerine dönüştürmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d8e30-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="d8e30-139">Yalnızca tarafından 1.0, 1.0 boyutları uygulama çarpın.</span><span class="sxs-lookup"><span data-stu-id="d8e30-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="d8e30-140">Bu gibi bir işlev uygulamasına soyutlamak `degreesFahrenheit`.</span><span class="sxs-lookup"><span data-stu-id="d8e30-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="d8e30-141">Ayrıca, dimensioned değerlerini dimensionless kayan noktalı sayıları beklediğiniz bir işleve geçirdiğinizde, birimi iptal etmeli veya başvurusuna `float` kullanarak `float` işleci.</span><span class="sxs-lookup"><span data-stu-id="d8e30-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="d8e30-142">Bu örnekte, bölen `1.0<degC>` bağımsız değişkenleri için `printf` çünkü `printf` dimensionless miktarlar bekliyor.</span><span class="sxs-lookup"><span data-stu-id="d8e30-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="d8e30-143">Aşağıdaki örnekte oturum bu kodu girişleri ve çıkışları gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8e30-143">The following example session shows the outputs from and inputs to this code.</span></span>

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="d8e30-144">Genel birimler</span><span class="sxs-lookup"><span data-stu-id="d8e30-144">Using Generic Units</span></span>
<span data-ttu-id="d8e30-145">İlişkili bir ölçü olan veriler üzerinde çalışan genel işlevler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8e30-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="d8e30-146">Bir tür parametresi bir türle birlikte genel bir birim belirterek aşağıdaki kod örneğinde gösterildiği gibi yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="d8e30-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]
    
## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="d8e30-147">Toplama türlerini genel birimleri ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="d8e30-147">Creating Aggregate Types with Generic Units</span></span>
<span data-ttu-id="d8e30-148">Aşağıdaki kod genel birimler sahip tek kayan nokta değerleri oluşan bir toplama türünü oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8e30-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="d8e30-149">Bu, çeşitli birimleri ile birlikte çalışan oluşturulacak tek bir türü sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8e30-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="d8e30-150">Ayrıca, genel birimleri tür güvenliği birimleri bir dizi olan bir genel tür birimleri farklı bir dizi ile aynı genel tür farklı bir tür olduğundan emin olarak korur.</span><span class="sxs-lookup"><span data-stu-id="d8e30-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="d8e30-151">Bu teknik temelini `Measure` özniteliği tür parametresi için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="d8e30-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]
    
## <a name="units-at-runtime"></a><span data-ttu-id="d8e30-152">Çalışma zamanında birimleri</span><span class="sxs-lookup"><span data-stu-id="d8e30-152">Units at Runtime</span></span>
<span data-ttu-id="d8e30-153">Ölçü birimleri statik tür denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8e30-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="d8e30-154">Kayan nokta değerleri derlendiğinde çalışma zamanında birimleri kayıp olacak şekilde ölçü, ortadan kalkar.</span><span class="sxs-lookup"><span data-stu-id="d8e30-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="d8e30-155">Bu nedenle, her türlü girişim çalışma zamanında birim denetimini bağlıdır işlevselliği uygulamak için mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="d8e30-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="d8e30-156">Örneğin, uygulama bir `ToString` işlevi birimi yazdırmak için mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="d8e30-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>


## <a name="conversions"></a><span data-ttu-id="d8e30-157">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="d8e30-157">Conversions</span></span>
<span data-ttu-id="d8e30-158">Birimleri olan bir türü dönüştürmek için (örneğin, `float<'u>`) birimleri sahip olmayan bir türe standart dönüştürme işlevini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8e30-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="d8e30-159">Örneğin, kullanabileceğiniz `float` dönüştürmek için bir `float` birimleri, aşağıdaki kodda gösterildiği gibi yok değeri.</span><span class="sxs-lookup"><span data-stu-id="d8e30-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="d8e30-160">Unitless değeri birimleri olan bir değere dönüştürülecek uygun birimleri ile açıklanıyor 1 veya 1.0 değere göre çarpabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8e30-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="d8e30-161">Ancak, birlikte çalışabilirlik katmanları yazmak için de bazı açık unitless değerleri birimleriyle değerlerine dönüştürmek için kullanabileceğiniz işlevi vardır.</span><span class="sxs-lookup"><span data-stu-id="d8e30-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="d8e30-162">İçinde bunlar [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modülü.</span><span class="sxs-lookup"><span data-stu-id="d8e30-162">These are in the [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module.</span></span> <span data-ttu-id="d8e30-163">Örneğin, unitless dönüştürmek için `float` için bir `float<cm>`, kullanın [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9)aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d8e30-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]
    
## <a name="units-of-measure-in-the-f-core-library"></a><span data-ttu-id="d8e30-164">F # çekirdek Kitaplığı'nda ölçü birimleri</span><span class="sxs-lookup"><span data-stu-id="d8e30-164">Units of Measure in the F# Core library</span></span>
<span data-ttu-id="d8e30-165">Bir birim kitaplığı kullanılabilir `FSharp.Data.UnitSystems.SI` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d8e30-165">A unit library is available in the `FSharp.Data.UnitSystems.SI` namespace.</span></span> <span data-ttu-id="d8e30-166">Bunların her iki simge biçiminde sı birimleri içerir (gibi `m` ölçüm için) içinde `UnitSymbols` alt ad alanı ve bunların tam adı (gibi `meter` ölçüm için) içinde `UnitNames` alt ad.</span><span class="sxs-lookup"><span data-stu-id="d8e30-166">It includes SI units in both their symbol form (like `m` for meter) in the `UnitSymbols` sub-namespace, and their full name (like `meter` for meter) in the `UnitNames` sub-namespace.</span></span>


## <a name="see-also"></a><span data-ttu-id="d8e30-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8e30-167">See Also</span></span>
[<span data-ttu-id="d8e30-168">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d8e30-168">F# Language Reference</span></span>](index.md)
