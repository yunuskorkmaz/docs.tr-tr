---
title: Atama ve Dönüştürmeler (F#)
description: 'Nasıl F # programlama dili dönüşüm işleçleri çeşitli ilkel türler arasında aritmetik dönüşümler için sağladığını öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: ba3cbed91bf6510a34bcb7ba89d34b0ea6b82711
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564501"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="8c528-103">Atama ve Dönüştürmeler (F#)</span><span class="sxs-lookup"><span data-stu-id="8c528-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="8c528-104">Bu konu, F # tür dönüştürmeleri için destek açıklanır.</span><span class="sxs-lookup"><span data-stu-id="8c528-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="8c528-105">Aritmetik türleri</span><span class="sxs-lookup"><span data-stu-id="8c528-105">Arithmetic Types</span></span>
<span data-ttu-id="8c528-106">F # dönüşüm işleçleri için çeşitli ilkel türler arasında aritmetik dönüşümler gibi tamsayı ve kayan nokta türleri arasında sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c528-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="8c528-107">İntegral ve karakter dönüştürme işleçleri denetlediyseniz ve Denetlenmeyen forms; kayan nokta işleçler ve `enum` dönüşüm işleci yapın.</span><span class="sxs-lookup"><span data-stu-id="8c528-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="8c528-108">Unchecked forms tanımlanan `Microsoft.FSharp.Core.Operators` ve denetlenen forms tanımlanan `Microsoft.FSharp.Core.Operators.Checked`.</span><span class="sxs-lookup"><span data-stu-id="8c528-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="8c528-109">Checked forms taşma durumunu denetleyin ve hedef türü sınırları sonuç değeri aşarsa, bir çalışma zamanı özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c528-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="8c528-110">Her bu işleçlerinin hedef türünün adı ile aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="8c528-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="8c528-111">Hangi türleri açıkça açıklama, örneğin, aşağıdaki kodda, `byte` ile iki farklı anlamları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8c528-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="8c528-112">Birinci türü ve ikinci dönüştürme işleci.</span><span class="sxs-lookup"><span data-stu-id="8c528-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="8c528-113">Aşağıdaki tabloda, F #'de tanımlanan dönüştürme işleçleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c528-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="8c528-114">İşleç</span><span class="sxs-lookup"><span data-stu-id="8c528-114">Operator</span></span>|<span data-ttu-id="8c528-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c528-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="8c528-116">Bir 8 bit işaretsiz tür bayta dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8c528-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="8c528-117">İmzalı bayta dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8c528-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="8c528-118">Bir 16 bit işaretli tamsayıyı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8c528-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="8c528-119">Bir 16 bit işaretsiz tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8c528-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="8c528-120">Bir 32 bit işaretli tamsayıyı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8c528-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="8c528-121">32-bit işaretsiz tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8c528-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="8c528-122">Bir 64-bit işaretli tamsayıyı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8c528-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="8c528-123">Bir 64-bit işaretsiz tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8c528-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="8c528-124">Yerel bir tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8c528-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="8c528-125">İmzasız yerel tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8c528-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="8c528-126">Bir 64-bit çift duyarlıklı IEEE kayan noktalı sayıyı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8c528-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="8c528-127">Bir 32-bit tek duyarlıklı IEEE kayan noktalı sayıyı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8c528-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="8c528-128">Dönüştür `System.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="8c528-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="8c528-129">Dönüştür `System.Char`, Unicode karakter.</span><span class="sxs-lookup"><span data-stu-id="8c528-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="8c528-130">Bir numaralandırılmış türüne dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8c528-130">Convert to an enumerated type.</span></span>|
<span data-ttu-id="8c528-131">Ek olarak yerleşik ilkel türler, uygulama türleri ile bu işleçleri kullanabilirsiniz `op_Explicit` veya `op_Implicit` uygun imzaları yöntemleriyle.</span><span class="sxs-lookup"><span data-stu-id="8c528-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="8c528-132">Örneğin, `int` dönüştürme işleci çalışır bir statik yöntem sağlar herhangi bir türü `op_Explicit` , türünü bir parametre olarak alıp döndüren `int`.</span><span class="sxs-lookup"><span data-stu-id="8c528-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="8c528-133">Yöntemleri tarafından dönüş türü aşırı genel kural için bir özel durum bunu yapabilmeniz `op_Explicit` ve `op_Implicit`.</span><span class="sxs-lookup"><span data-stu-id="8c528-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="8c528-134">Numaralandırılmış türler</span><span class="sxs-lookup"><span data-stu-id="8c528-134">Enumerated Types</span></span>
<span data-ttu-id="8c528-135">`enum` İşlecidir türünü temsil eden bir tür parametre alan genel bir işleç `enum` dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="8c528-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="8c528-136">Numaralandırılmış bir türe dönüştürür, çıkarım türünü belirleme girişimleri yazın `enum` dönüştürmek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="8c528-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="8c528-137">Aşağıdaki örnekte, değişken `col1` açıkça açıklama değil, ancak türü sonraki eşitlik testten algılanır.</span><span class="sxs-lookup"><span data-stu-id="8c528-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="8c528-138">Bu nedenle, derleyici için dönüştürüyorsunuz türetme bir `Color` numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="8c528-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="8c528-139">Alternatif olarak, bir tür ek açıklama sağlayabilir olduğu gibi `col2` aşağıdaki örnekte.</span><span class="sxs-lookup"><span data-stu-id="8c528-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]
    
<span data-ttu-id="8c528-140">Ayrıca hedef numaralandırma türü açıkça aşağıdaki kodu olduğu gibi bir tür parametresi olarak belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8c528-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="8c528-141">Yalnızca sabit temel alınan türü dönüştürülmekte olan türü ile uyumlu ise numaralandırması iş çevirir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8c528-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="8c528-142">Aşağıdaki kodda arasındaki uyumsuzluk nedeniyle derlemek dönüştürme başarısız `int32` ve `uint32`.</span><span class="sxs-lookup"><span data-stu-id="8c528-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="8c528-143">Daha fazla bilgi için bkz: [numaralandırmalar](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="8c528-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="8c528-144">Nesne türlerini dönüştürmeyi</span><span class="sxs-lookup"><span data-stu-id="8c528-144">Casting Object Types</span></span>
<span data-ttu-id="8c528-145">Bir nesne hiyerarşideki türleri arasında dönüştürme nesne odaklı programlama için temel önemdedir.</span><span class="sxs-lookup"><span data-stu-id="8c528-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="8c528-146">İki temel tür dönüşümleri vardır: (üst türe çevirme) atama ve (alt türe çevirme) atama.</span><span class="sxs-lookup"><span data-stu-id="8c528-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="8c528-147">Bir hiyerarşi atama temel nesne başvurusu için bir türetilen nesne başvurusundan atama anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8c528-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="8c528-148">Bu tür bir cast türetilmiş sınıf devralma hiyerarşisini temel sınıftır sürece çalışmak için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8c528-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="8c528-149">Yalnızca nesne örneği (türetilmiş) doğru hedef türü veya hedef türden türetilmiş bir tür gerçekte ise bir hiyerarşiden bir türetilen nesne başvurusu bir temel nesne başvurusu aşağı atama başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="8c528-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="8c528-150">F # işleçleri bu tür dönüştürmeleri için sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c528-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="8c528-151">`:>` İşleci çevirir hiyerarşisinde yukarı ve `:?>` işleci hiyerarşide aşağıda çevirir.</span><span class="sxs-lookup"><span data-stu-id="8c528-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="8c528-152">Üst türe çevirme</span><span class="sxs-lookup"><span data-stu-id="8c528-152">Upcasting</span></span>
<span data-ttu-id="8c528-153">Birçok nesne yönelimli dilde üst türe çevirme örtük; F #'ta kuralları biraz farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c528-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="8c528-154">Bir nesne türü yöntemleri için bağımsız değişken geçirdiğinizde üst türe çevirme otomatik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8c528-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="8c528-155">Parametre türü esnek bir türü olarak bildirilmiş sürece ancak, bir modüldeki let bağlı işlevleri için üst türe çevirme otomatik, değildir.</span><span class="sxs-lookup"><span data-stu-id="8c528-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="8c528-156">Daha fazla bilgi için bkz: [esnek türler](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="8c528-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="8c528-157">`:>` İşleci cast, cast başarısını derleme zamanında belirlenir başka bir deyişle, statik gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8c528-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="8c528-158">Kullanan bir cast varsa `:>` başarıyla derlenen geçerli bir cast olduğundan ve hiçbir sıkıştırılabilmesi çalışma zamanında hata.</span><span class="sxs-lookup"><span data-stu-id="8c528-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="8c528-159">Aynı zamanda `upcast` böyle bir dönüştürme gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="8c528-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="8c528-160">Aşağıdaki ifade, hiyerarşi içinde yukarı doğru bir dönüştürme belirtir:</span><span class="sxs-lookup"><span data-stu-id="8c528-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="8c528-161">Upcast işleci kullandığınızda, derleyici bağlamdan dönüştürüyorsunuz türü Infer dener.</span><span class="sxs-lookup"><span data-stu-id="8c528-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="8c528-162">Derleyici hedef türü belirlenemiyor ise derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="8c528-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="8c528-163">Alt türe çevirme</span><span class="sxs-lookup"><span data-stu-id="8c528-163">Downcasting</span></span>
<span data-ttu-id="8c528-164">`:?>` İşleci cast, cast başarısını çalışma zamanında belirlenir yani dinamik gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8c528-164">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="8c528-165">Kullanan bir cast `:?>` işleci derleme zamanında; işaretlenmediği ancak çalışma zamanında denemesi belirtilen türe için yapılır.</span><span class="sxs-lookup"><span data-stu-id="8c528-165">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="8c528-166">Nesne hedef türü ile uyumlu ise, cast başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="8c528-166">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="8c528-167">Nesne hedef türü ile uyumlu değilse, çalışma zamanı başlatır bir `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="8c528-167">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="8c528-168">Aynı zamanda `downcast` dinamik tür dönüştürme gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="8c528-168">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="8c528-169">Aşağıdaki ifade program bağlamından çıkarımı yapılan tür hiyerarşide aşağı bir dönüştürme belirtir:</span><span class="sxs-lookup"><span data-stu-id="8c528-169">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="8c528-170">Olarak `upcast` işleci, derleyici bağlamı belirli hedef türünden gösterilemez, rapor hata.</span><span class="sxs-lookup"><span data-stu-id="8c528-170">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="8c528-171">Aşağıdaki kod kullanımını göstermektedir `:>` ve `:?>` işleçler.</span><span class="sxs-lookup"><span data-stu-id="8c528-171">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="8c528-172">Kod gösterir `:?>` işleci oluşturur, çünkü dönüştürme başarılı olur olduğunu bildiğiniz durumlarda en iyi şekilde kullanılan `InvalidCastException` dönüştürme başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="8c528-172">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="8c528-173">Dönüştürme başarılı olur, kullanan bir tür testini bilmiyorsanız bir `match` ifade olduğundan daha iyi bir özel durum oluşturma yükünü ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8c528-173">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="8c528-174">Çünkü genel işleçler `downcast` ve `upcast` tür çıkarımı bağımsız değişkeni ve dönüş türü Yukarıdaki kod belirlemek için kullanır, değiştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="8c528-174">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="8c528-175">örneklerini şununla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="8c528-175">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="8c528-176">Önceki kod içinde bağımsız değişken türü ve dönüş türleri olan `Derived1` ve `Base1`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="8c528-176">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="8c528-177">Türü testleri hakkında daha fazla bilgi için bkz: [eşleşme ifadeleri](match-Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8c528-177">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8c528-178">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c528-178">See Also</span></span>
[<span data-ttu-id="8c528-179">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8c528-179">F# Language Reference</span></span>](index.md)
