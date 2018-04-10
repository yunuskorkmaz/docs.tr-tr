---
title: Atama ve Dönüştürmeler (F#)
description: 'Nasıl F # programlama dili dönüşüm işleçleri çeşitli ilkel türler arasında aritmetik dönüşümler için sağladığını öğrenin.'
keywords: 'Visual f #, f # işlevsel programlama'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: db30db67-da21-4206-bf0c-9211bd3cb22f
ms.openlocfilehash: df8352b0dd8651f1480515311454a218ea79b971
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="d99ef-104">Atama ve Dönüştürmeler (F#)</span><span class="sxs-lookup"><span data-stu-id="d99ef-104">Casting and Conversions (F#)</span></span>

<span data-ttu-id="d99ef-105">Bu konu, F # tür dönüştürmeleri için destek açıklanır.</span><span class="sxs-lookup"><span data-stu-id="d99ef-105">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="d99ef-106">Aritmetik türleri</span><span class="sxs-lookup"><span data-stu-id="d99ef-106">Arithmetic Types</span></span>
<span data-ttu-id="d99ef-107">F # dönüşüm işleçleri için çeşitli ilkel türler arasında aritmetik dönüşümler gibi tamsayı ve kayan nokta türleri arasında sağlar.</span><span class="sxs-lookup"><span data-stu-id="d99ef-107">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="d99ef-108">İntegral ve karakter dönüştürme işleçleri denetlediyseniz ve Denetlenmeyen forms; kayan nokta işleçler ve `enum` dönüşüm işleci yapın.</span><span class="sxs-lookup"><span data-stu-id="d99ef-108">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="d99ef-109">Unchecked forms tanımlanan `Microsoft.FSharp.Core.Operators` ve denetlenen forms tanımlanan `Microsoft.FSharp.Core.Operators.Checked`.</span><span class="sxs-lookup"><span data-stu-id="d99ef-109">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="d99ef-110">Checked forms taşma durumunu denetleyin ve hedef türü sınırları sonuç değeri aşarsa, bir çalışma zamanı özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d99ef-110">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="d99ef-111">Her bu işleçlerinin hedef türünün adı ile aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="d99ef-111">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="d99ef-112">Hangi türleri açıkça açıklama, örneğin, aşağıdaki kodda, `byte` ile iki farklı anlamları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d99ef-112">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="d99ef-113">Birinci türü ve ikinci dönüştürme işleci.</span><span class="sxs-lookup"><span data-stu-id="d99ef-113">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="d99ef-114">Aşağıdaki tabloda, F #'de tanımlanan dönüştürme işleçleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d99ef-114">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="d99ef-115">İşleç</span><span class="sxs-lookup"><span data-stu-id="d99ef-115">Operator</span></span>|<span data-ttu-id="d99ef-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d99ef-116">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="d99ef-117">Bir 8 bit işaretsiz tür bayta dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="d99ef-117">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="d99ef-118">İmzalı bayta dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="d99ef-118">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="d99ef-119">Bir 16 bit işaretli tamsayıyı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="d99ef-119">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="d99ef-120">Bir 16 bit işaretsiz tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d99ef-120">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="d99ef-121">Bir 32 bit işaretli tamsayıyı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="d99ef-121">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="d99ef-122">32-bit işaretsiz tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d99ef-122">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="d99ef-123">Bir 64-bit işaretli tamsayıyı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="d99ef-123">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="d99ef-124">Bir 64-bit işaretsiz tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d99ef-124">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="d99ef-125">Yerel bir tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d99ef-125">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="d99ef-126">İmzasız yerel tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d99ef-126">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="d99ef-127">Bir 64-bit çift duyarlıklı IEEE kayan noktalı sayıyı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="d99ef-127">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="d99ef-128">Bir 32-bit tek duyarlıklı IEEE kayan noktalı sayıyı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="d99ef-128">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="d99ef-129">Dönüştür `System.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d99ef-129">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="d99ef-130">Dönüştür `System.Char`, Unicode karakter.</span><span class="sxs-lookup"><span data-stu-id="d99ef-130">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="d99ef-131">Bir numaralandırılmış türüne dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="d99ef-131">Convert to an enumerated type.</span></span>|
<span data-ttu-id="d99ef-132">Ek olarak yerleşik ilkel türler, uygulama türleri ile bu işleçleri kullanabilirsiniz `op_Explicit` veya `op_Implicit` uygun imzaları yöntemleriyle.</span><span class="sxs-lookup"><span data-stu-id="d99ef-132">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="d99ef-133">Örneğin, `int` dönüştürme işleci çalışır bir statik yöntem sağlar herhangi bir türü `op_Explicit` , türünü bir parametre olarak alıp döndüren `int`.</span><span class="sxs-lookup"><span data-stu-id="d99ef-133">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="d99ef-134">Yöntemleri tarafından dönüş türü aşırı genel kural için bir özel durum bunu yapabilmeniz `op_Explicit` ve `op_Implicit`.</span><span class="sxs-lookup"><span data-stu-id="d99ef-134">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="d99ef-135">Numaralandırılmış türler</span><span class="sxs-lookup"><span data-stu-id="d99ef-135">Enumerated Types</span></span>
<span data-ttu-id="d99ef-136">`enum` İşlecidir türünü temsil eden bir tür parametre alan genel bir işleç `enum` dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="d99ef-136">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="d99ef-137">Numaralandırılmış bir türe dönüştürür, çıkarım türünü belirleme girişimleri yazın `enum` dönüştürmek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="d99ef-137">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="d99ef-138">Aşağıdaki örnekte, değişken `col1` açıkça açıklama değil, ancak türü sonraki eşitlik testten algılanır.</span><span class="sxs-lookup"><span data-stu-id="d99ef-138">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="d99ef-139">Bu nedenle, derleyici için dönüştürüyorsunuz türetme bir `Color` numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="d99ef-139">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="d99ef-140">Alternatif olarak, bir tür ek açıklama sağlayabilir olduğu gibi `col2` aşağıdaki örnekte.</span><span class="sxs-lookup"><span data-stu-id="d99ef-140">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]
    
<span data-ttu-id="d99ef-141">Ayrıca hedef numaralandırma türü açıkça aşağıdaki kodu olduğu gibi bir tür parametresi olarak belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d99ef-141">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="d99ef-142">Yalnızca sabit temel alınan türü dönüştürülmekte olan türü ile uyumlu ise numaralandırması iş çevirir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d99ef-142">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="d99ef-143">Aşağıdaki kodda arasındaki uyumsuzluk nedeniyle derlemek dönüştürme başarısız `int32` ve `uint32`.</span><span class="sxs-lookup"><span data-stu-id="d99ef-143">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="d99ef-144">Daha fazla bilgi için bkz: [numaralandırmalar](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="d99ef-144">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="d99ef-145">Nesne türlerini dönüştürmeyi</span><span class="sxs-lookup"><span data-stu-id="d99ef-145">Casting Object Types</span></span>
<span data-ttu-id="d99ef-146">Bir nesne hiyerarşideki türleri arasında dönüştürme nesne odaklı programlama için temel önemdedir.</span><span class="sxs-lookup"><span data-stu-id="d99ef-146">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="d99ef-147">İki temel tür dönüşümleri vardır: (üst türe çevirme) atama ve (alt türe çevirme) atama.</span><span class="sxs-lookup"><span data-stu-id="d99ef-147">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="d99ef-148">Bir hiyerarşi atama temel nesne başvurusu için bir türetilen nesne başvurusundan atama anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d99ef-148">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="d99ef-149">Bu tür bir cast türetilmiş sınıf devralma hiyerarşisini temel sınıftır sürece çalışmak için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d99ef-149">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="d99ef-150">Yalnızca nesne örneği (türetilmiş) doğru hedef türü veya hedef türden türetilmiş bir tür gerçekte ise bir hiyerarşiden bir türetilen nesne başvurusu bir temel nesne başvurusu aşağı atama başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="d99ef-150">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="d99ef-151">F # işleçleri bu tür dönüştürmeleri için sağlar.</span><span class="sxs-lookup"><span data-stu-id="d99ef-151">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="d99ef-152">`:>` İşleci çevirir hiyerarşisinde yukarı ve `:?>` işleci hiyerarşide aşağıda çevirir.</span><span class="sxs-lookup"><span data-stu-id="d99ef-152">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="d99ef-153">Üst türe çevirme</span><span class="sxs-lookup"><span data-stu-id="d99ef-153">Upcasting</span></span>
<span data-ttu-id="d99ef-154">Birçok nesne yönelimli dilde üst türe çevirme örtük; F #'ta kuralları biraz farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="d99ef-154">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="d99ef-155">Bir nesne türü yöntemleri için bağımsız değişken geçirdiğinizde üst türe çevirme otomatik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d99ef-155">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="d99ef-156">Parametre türü esnek bir türü olarak bildirilmiş sürece ancak, bir modüldeki let bağlı işlevleri için üst türe çevirme otomatik, değildir.</span><span class="sxs-lookup"><span data-stu-id="d99ef-156">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="d99ef-157">Daha fazla bilgi için bkz: [esnek türler](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="d99ef-157">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="d99ef-158">`:>` İşleci cast, cast başarısını derleme zamanında belirlenir başka bir deyişle, statik gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d99ef-158">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="d99ef-159">Kullanan bir cast varsa `:>` başarıyla derlenen geçerli bir cast olduğundan ve hiçbir sıkıştırılabilmesi çalışma zamanında hata.</span><span class="sxs-lookup"><span data-stu-id="d99ef-159">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="d99ef-160">Aynı zamanda `upcast` böyle bir dönüştürme gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="d99ef-160">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="d99ef-161">Aşağıdaki ifade, hiyerarşi içinde yukarı doğru bir dönüştürme belirtir:</span><span class="sxs-lookup"><span data-stu-id="d99ef-161">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="d99ef-162">Upcast işleci kullandığınızda, derleyici bağlamdan dönüştürüyorsunuz türü Infer dener.</span><span class="sxs-lookup"><span data-stu-id="d99ef-162">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="d99ef-163">Derleyici hedef türü belirlenemiyor ise derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="d99ef-163">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="d99ef-164">Alt türe çevirme</span><span class="sxs-lookup"><span data-stu-id="d99ef-164">Downcasting</span></span>
<span data-ttu-id="d99ef-165">`:?>` İşleci cast, cast başarısını çalışma zamanında belirlenir yani dinamik gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d99ef-165">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="d99ef-166">Kullanan bir cast `:?>` işleci derleme zamanında; işaretlenmediği ancak çalışma zamanında denemesi belirtilen türe için yapılır.</span><span class="sxs-lookup"><span data-stu-id="d99ef-166">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="d99ef-167">Nesne hedef türü ile uyumlu ise, cast başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="d99ef-167">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="d99ef-168">Nesne hedef türü ile uyumlu değilse, çalışma zamanı başlatır bir `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="d99ef-168">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="d99ef-169">Aynı zamanda `downcast` dinamik tür dönüştürme gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="d99ef-169">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="d99ef-170">Aşağıdaki ifade program bağlamından çıkarımı yapılan tür hiyerarşide aşağı bir dönüştürme belirtir:</span><span class="sxs-lookup"><span data-stu-id="d99ef-170">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="d99ef-171">Olarak `upcast` işleci, derleyici bağlamı belirli hedef türünden gösterilemez, rapor hata.</span><span class="sxs-lookup"><span data-stu-id="d99ef-171">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="d99ef-172">Aşağıdaki kod kullanımını göstermektedir `:>` ve `:?>` işleçler.</span><span class="sxs-lookup"><span data-stu-id="d99ef-172">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="d99ef-173">Kod gösterir `:?>` işleci oluşturur, çünkü dönüştürme başarılı olur olduğunu bildiğiniz durumlarda en iyi şekilde kullanılan `InvalidCastException` dönüştürme başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="d99ef-173">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="d99ef-174">Dönüştürme başarılı olur, kullanan bir tür testini bilmiyorsanız bir `match` ifade olduğundan daha iyi bir özel durum oluşturma yükünü ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d99ef-174">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="d99ef-175">Çünkü genel işleçler `downcast` ve `upcast` tür çıkarımı bağımsız değişkeni ve dönüş türü Yukarıdaki kod belirlemek için kullanır, değiştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="d99ef-175">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="d99ef-176">örneklerini şununla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d99ef-176">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="d99ef-177">Önceki kod içinde bağımsız değişken türü ve dönüş türleri olan `Derived1` ve `Base1`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="d99ef-177">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="d99ef-178">Türü testleri hakkında daha fazla bilgi için bkz: [eşleşme ifadeleri](match-Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d99ef-178">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d99ef-179">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d99ef-179">See Also</span></span>
[<span data-ttu-id="d99ef-180">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d99ef-180">F# Language Reference</span></span>](index.md)
