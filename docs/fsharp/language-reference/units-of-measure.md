---
title: Ölçü Birimleri
description: İçindeki F# kayan nokta ve işaretli tamsayı değerlerinin, genellikle uzunluğu, hacmi ve kütle belirtmek için kullanılan, ilişkili ölçü birimlerine nasıl sahip olabileceğini öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: f97eac9984f934c55aff8cf9f287afbc3aa098f3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630164"
---
# <a name="units-of-measure"></a><span data-ttu-id="8b3c1-103">Ölçü Birimleri</span><span class="sxs-lookup"><span data-stu-id="8b3c1-103">Units of Measure</span></span>

<span data-ttu-id="8b3c1-104">İçindeki F# kayan nokta ve işaretli tamsayı değerleri, genellikle uzunluğu, hacmi, kütle, vb. belirtmek için kullanılan, ilişkili ölçü birimlerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="8b3c1-105">Birimleri olan miktarları kullanarak, aritmetik ilişkilerin doğru birimlere sahip olduğunu doğrulamak için derleyicinin, programlama hatalarının önlenmesine yardımcı olan doğru birimlere sahip olduğunu doğrulaması için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="8b3c1-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b3c1-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="8b3c1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b3c1-107">Remarks</span></span>

<span data-ttu-id="8b3c1-108">Önceki sözdizimi *birim adını* ölçü birimi olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="8b3c1-109">İsteğe bağlı bölüm, önceden tanımlanmış birimler açısından yeni bir ölçü tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="8b3c1-110">Örneğin, aşağıdaki satır ölçüyü `cm` (santimeter) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="8b3c1-111">Aşağıdaki satır, ölçüyü `ml` (milliliter) santimetrede (`cm^3`) olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="8b3c1-112">Önceki sözdiziminde, *Ölçü* birimleri içeren bir formüldür.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="8b3c1-113">Birimleri içeren formüllerde, tam sayı güçleri desteklenir (pozitif ve negatif), birimler arasındaki boşluklar iki birimin bir ürününü belirtir, `*` Ayrıca bir birim ürünü gösterir ve `/` birim bölümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="8b3c1-114">Ters bir birim için, bir birim formülünün pay ve paydası arasındaki ayrımı belirten `/` negatif bir tamsayı gücü veya bir kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="8b3c1-115">Paydadaki birden çok birim parantezle çevrelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="8b3c1-116">Bir değeri paydaya bir `/` parçası olarak yorumlandıktan sonra boşluklara göre ayrılmış birimler, ancak bir sonraki birimler, payın bir `*` parçası olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="8b3c1-117">Birim ifadelerinde 1 ' i, bir boyutsuz miktarı belirtmek için tek başına ya da pay içindeki gibi diğer birimlerle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="8b3c1-118">Örneğin, bir hız için birimler olarak `1/s`yazılır; burada `s` saniyeler belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="8b3c1-119">Parantezler, birim formüllerinde kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="8b3c1-120">Birim formüllerinde sayısal dönüştürme sabitleri belirtmeyin; Ancak, birimlere ayrı olarak dönüştürme sabitleri tanımlayabilir ve bunları birim denetimli hesaplamalar halinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="8b3c1-121">Aynı şeyi gösteren birim formülleri, çeşitli eşdeğer yollarla yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="8b3c1-122">Bu nedenle, derleyici birim formüllerini, negatif üsleri devrik bir biçimde, gruplar birimlerini tek bir pay ve paydaya dönüştürür ve pay ve paydadaki birimleri alfabetik hale getirir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="8b3c1-123">Örneğin, birim formülleri `kg m s^-2` ve `m /s s * kg` her ikisi de olarak `kg m/s^2`dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="8b3c1-124">Kayan nokta ifadelerinde ölçü birimleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="8b3c1-125">İlişkili ölçü birimleriyle birlikte kayan noktalı sayıların kullanılması, başka bir tür güvenliği düzeyi ekler ve zayıf yazılmış kayan noktalı sayılar kullandığınızda formüllerde oluşabilecek birim uyumsuzluğu hatalarından kaçınmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="8b3c1-126">Birimleri kullanan bir kayan nokta ifadesi yazarsanız, ifadedeki birimlerin eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="8b3c1-127">Aşağıdaki örneklerde gösterildiği gibi, bir birim formülüyle, açılı ayraç içinde sabit değerlere açıklama ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="8b3c1-128">Sayı ve açılı ayraç arasına bir boşluk koymayın; Ancak, aşağıdaki örnekte olduğu gibi `f`, gibi bir sabit sonek dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="8b3c1-129">Böyle bir ek açıklama, değişmez değer türünü (gibi `float`) temel türünden veya `float<miles/hour>`gibi `float<cm>` bir boyut türüne (örneğin,) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="8b3c1-130">Bir birim ek açıklaması `<1>` , bir boyutsuz miktarı gösterir ve türü bir birim parametresi olmadan temel tür ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="8b3c1-131">Bir ölçü biriminin türü, parantez içinde belirtilen ek birim ek açıklaması ile birlikte bir kayan nokta veya imzalı integral türüdür.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="8b3c1-132">Bu nedenle, (gram `g` `kg` ) ' den (kilogram) dönüştürme türünü yazdığınızda, türleri aşağıdaki şekilde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="8b3c1-133">Ölçü birimleri derleme zamanı birim denetlemesi için kullanılır, ancak çalışma zamanı ortamında kalıcı değildir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="8b3c1-134">Bu nedenle, performansı etkilemezler.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="8b3c1-135">Ölçü birimleri yalnızca kayan nokta türleri değil herhangi bir türe uygulanabilir; Ancak, yalnızca kayan nokta türleri, işaretli integral türleri ve ondalık türler boyutlanır miktarları destekler.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="8b3c1-136">Bu nedenle, yalnızca temel türler ve bu ilkel türleri içeren toplamalarda ölçü birimleri kullanmak mantıklı olur.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="8b3c1-137">Aşağıdaki örnek ölçü birimlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

<span data-ttu-id="8b3c1-138">Aşağıdaki kod örneği, bir boyutsuz kayan nokta numarasından bir boyutlandırma kayan nokta değerine nasıl dönüştürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="8b3c1-139">1,0 ile çarpıp, boyutları 1,0 ' ye uygulayarak yapmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="8b3c1-140">Bunu, gibi `degreesFahrenheit`bir işlev içinde soyut hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="8b3c1-141">Ayrıca, boyutlandırma değerlerini boyutsuz kayan noktalı sayılar bekleyen işlevlere geçirdiğinizde birimi iptal etmeniz veya `float` `float` işlecini kullanarak atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="8b3c1-142">Bu örnekte, için ' a kadar `1.0<degC>` olan bağımsız değişkenler, `printf` boyutsuz miktarlar gerektirdiğinden `printf` öğesine göre bölmektir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="8b3c1-143">Aşağıdaki örnek oturum, bu koda ait çıkış ve giriş gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-143">The following example session shows the outputs from and inputs to this code.</span></span>

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="8b3c1-144">Genel birimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="8b3c1-144">Using Generic Units</span></span>

<span data-ttu-id="8b3c1-145">İlişkili ölçü birimi olan veriler üzerinde çalışan genel işlevler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="8b3c1-146">Bunu, aşağıdaki kod örneğinde gösterildiği gibi, bir türü bir genel birimle birlikte bir tür parametresi olarak belirterek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="8b3c1-147">Genel birimlerle toplama türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b3c1-147">Creating Aggregate Types with Generic Units</span></span>

<span data-ttu-id="8b3c1-148">Aşağıdaki kod, genel birimlere sahip bağımsız kayan nokta değerlerinden oluşan bir toplam türün nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="8b3c1-149">Bu, çeşitli birimlerle birlikte çalışarak tek bir türün oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="8b3c1-150">Ayrıca, genel birimler, tek bir birim kümesine sahip genel bir türün farklı bir birim kümesiyle aynı genel türden farklı türde olmasını sağlayarak tür güvenliğini korur.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="8b3c1-151">Bu tekniğin `Measure` temeli özniteliğin tür parametresine uygulanabilirler.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a><span data-ttu-id="8b3c1-152">Çalışma zamanında birimler</span><span class="sxs-lookup"><span data-stu-id="8b3c1-152">Units at Runtime</span></span>

<span data-ttu-id="8b3c1-153">Ölçü birimleri statik tür denetlemesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="8b3c1-154">Kayan nokta değerleri derlendiğinde, ölçü birimleri ortadan kaldırılır, bu nedenle birimler çalışma zamanında kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="8b3c1-155">Bu nedenle, çalışma zamanında birimleri denetlemeye bağlı olan işlevleri uygulama girişimi mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="8b3c1-156">Örneğin, birimleri yazdırmak için `ToString` bir işlev uygulamak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>

## <a name="conversions"></a><span data-ttu-id="8b3c1-157">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="8b3c1-157">Conversions</span></span>

<span data-ttu-id="8b3c1-158">Birimleri olan bir türü (örneğin, `float<'u>`) birimi olmayan bir türe dönüştürmek için Standart dönüştürme işlevini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="8b3c1-159">Örneğin, aşağıdaki kodda gösterildiği gibi `float` , birimi olmayan bir `float` değere dönüştürmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="8b3c1-160">Bir unitless değerini birimlere sahip bir değere dönüştürmek için, uygun birimlerle açıklanmış bir 1 veya 1,0 değeri ile çarpmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="8b3c1-161">Bununla birlikte, birlikte çalışabilirlik katmanları yazmak için, birimsiz değerleri birimlere eşit değerlere dönüştürmek üzere kullanabileceğiniz bazı açık işlevler de vardır.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="8b3c1-162">Bunlar [Microsoft. FSharp. Core. LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modülüdür.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-162">These are in the [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module.</span></span> <span data-ttu-id="8b3c1-163">Örneğin, bir unitküçüktür `float` `float<cm>`öğesine dönüştürmek için aşağıdaki kodda gösterildiği gibi [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9)kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a><span data-ttu-id="8b3c1-164">F# Çekirdek kitaplığındaki ölçü birimleri</span><span class="sxs-lookup"><span data-stu-id="8b3c1-164">Units of Measure in the F# Core library</span></span>

<span data-ttu-id="8b3c1-165">`FSharp.Data.UnitSystems.SI` Ad alanında bir birim kitaplığı mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-165">A unit library is available in the `FSharp.Data.UnitSystems.SI` namespace.</span></span> <span data-ttu-id="8b3c1-166">Alt ad alanında hem sembol `m` biçiminde (ölçüm gibi) `UnitNames` `meter` hem de alt ad alanındaki tam adı (ölçüm için) olan sı birimleri içerir. `UnitSymbols`</span><span class="sxs-lookup"><span data-stu-id="8b3c1-166">It includes SI units in both their symbol form (like `m` for meter) in the `UnitSymbols` sub-namespace, and their full name (like `meter` for meter) in the `UnitNames` sub-namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b3c1-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b3c1-167">See also</span></span>

- [<span data-ttu-id="8b3c1-168">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8b3c1-168">F# Language Reference</span></span>](index.md)
