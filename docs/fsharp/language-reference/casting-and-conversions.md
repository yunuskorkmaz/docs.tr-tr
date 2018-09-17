---
title: Atama ve Dönüştürmeler (F#)
description: 'Nasıl F # programlama dilinin dönüştürme işleçleri çeşitli ilkel türler arasında aritmetik dönüştürmeler için sağladığını öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: aca1a2523130ee485a7e7c9a6a45a410904cb246
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677937"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="8ef6f-103">Atama ve Dönüştürmeler (F#)</span><span class="sxs-lookup"><span data-stu-id="8ef6f-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="8ef6f-104">Bu konu, F # tür dönüştürmeleri desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="8ef6f-105">Aritmetik tür</span><span class="sxs-lookup"><span data-stu-id="8ef6f-105">Arithmetic Types</span></span>

<span data-ttu-id="8ef6f-106">F # dönüştürme işleçleri için çeşitli ilkel türler arasında aritmetik dönüştürmeler gibi tamsayı ve kayan nokta türleri arasında sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="8ef6f-107">İntegral ve karakter dönüştürme işleçleri iade etmiş ve Denetlenmeyen forms; kayan nokta işleçler ve `enum` dönüştürme işleci yapın.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="8ef6f-108">Denetlenmeyen forms tanımlanan `Microsoft.FSharp.Core.Operators` ve işaretli forms tanımlanan `Microsoft.FSharp.Core.Operators.Checked`.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="8ef6f-109">İşaretli formları için taşmayı denetle ve sonuç değerini hedef türünün limitlerini aşarsam bir çalışma zamanı özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="8ef6f-110">Bu işleçlerden her biri, hedef türünün adı ile aynı ada sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="8ef6f-111">Hangi türleri açıkça ek açıklama, örneğin, aşağıdaki kodda, `byte` ile iki farklı anlamları görünür.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="8ef6f-112">İlk yinelenme türüdür ve ikincisi dönüştürme işleci.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="8ef6f-113">Aşağıdaki tabloda, F #'de tanımlanan dönüştürme işleçlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="8ef6f-114">İşleç</span><span class="sxs-lookup"><span data-stu-id="8ef6f-114">Operator</span></span>|<span data-ttu-id="8ef6f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ef6f-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="8ef6f-116">Bir 8 bit işaretsiz türe bayta dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="8ef6f-117">İmzalanan byte'a Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="8ef6f-118">16 bit işaretli bir tamsayıya dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="8ef6f-119">Bir 16 bitlik işaretsiz tamsayı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="8ef6f-120">32-bit işaretli bir tamsayıya dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="8ef6f-121">Bir 32-bit işaretsiz tamsayıyı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="8ef6f-122">Bir 64-bit işaretli bir tamsayıya dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="8ef6f-123">Bir 64-bit işaretsiz tamsayıyı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="8ef6f-124">Yerel bir tamsayıya dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="8ef6f-125">Yerel bir işaretsiz tamsayı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="8ef6f-126">Bir 64-bit çift duyarlıklı IEEE kayan noktalı sayı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="8ef6f-127">Bir 32-bit tek duyarlıklı IEEE kayan noktalı sayı dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="8ef6f-128">Dönüştürme `System.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="8ef6f-129">Dönüştürme `System.Char`, bir Unicode karakter.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="8ef6f-130">Numaralandırılmış bir türe dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-130">Convert to an enumerated type.</span></span>|
<span data-ttu-id="8ef6f-131">Ek olarak yerleşik temel türler, bu işleçler uygulayan türler ile kullanabilirsiniz `op_Explicit` veya `op_Implicit` uygun imzalara sahip yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="8ef6f-132">Örneğin, `int` çalışır bir statik yöntem sağlar herhangi bir tür dönüştürme işleci `op_Explicit` türü bir parametre olarak alır ve döndürür `int`.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="8ef6f-133">Yöntem dönüş türüne göre aşırı yüklenemez genel kural için bir özel durum bunu yapabilmeniz `op_Explicit` ve `op_Implicit`.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="8ef6f-134">Numaralandırılmış türler</span><span class="sxs-lookup"><span data-stu-id="8ef6f-134">Enumerated Types</span></span>

<span data-ttu-id="8ef6f-135">`enum` İşlecidir türünü temsil eden bir tür parametre alan bir genel işleç `enum` dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="8ef6f-136">Numaralandırılmış bir türe dönüştürürken türünü belirlemek için çıkarım denemeleri yazın `enum` dönüştürmek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="8ef6f-137">Aşağıdaki örnekte, değişken `col1` açıkça açıklama değil, ancak sonraki eşitlik testi türünü algılanır.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="8ef6f-138">Bu nedenle, derleyici için dönüştürdüğünüz çıkarabilir bir `Color` sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="8ef6f-139">Alternatif olarak, bir tür ek açıklamasına sağlayabilirsiniz olduğu gibi `col2` aşağıdaki örnekte.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

<span data-ttu-id="8ef6f-140">Hedef numaralandırma türüne açıkça aşağıdaki kodda gösterildiği gibi bir tür parametresi olarak belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8ef6f-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="8ef6f-141">Sabit listesi türünü temel dönüştürülen türü ile uyumlu ise sabit iş bıraktığı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="8ef6f-142">Aşağıdaki kodda, dönüştürme başarısız arasındaki uyumsuzluk nedeniyle derleme `int32` ve `uint32`.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="8ef6f-143">Daha fazla bilgi için [numaralandırmalar](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="8ef6f-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="8ef6f-144">Nesne türlerini atama</span><span class="sxs-lookup"><span data-stu-id="8ef6f-144">Casting Object Types</span></span>

<span data-ttu-id="8ef6f-145">Bir nesne sıradüzeni türleri arasında dönüştürme, nesne yönelimli programlama için temeldir.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="8ef6f-146">İki temel tür dönüştürmeleri vardır: (yukarı çevrim) atama ve atama (Alta).</span><span class="sxs-lookup"><span data-stu-id="8ef6f-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="8ef6f-147">Bir hiyerarşi atama temel nesne başvurusu için türetilmiş nesneden başvurudan atama anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="8ef6f-148">Böyle bir dönüştürme, temel sınıfın türetilmiş sınıf devralma hiyerarşisinde olduğu sürece çalışmak için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="8ef6f-149">Yalnızca nesne (türetilmiş) doğru hedef türüne veya hedef türünden türetilmiş bir tür örneği gerçekten ise bir hiyerarşiden bir türetilmiş nesne başvurusu bir temel nesne başvurusu aşağı atama başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="8ef6f-150">F # bu türde dönüştürme işleçleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="8ef6f-151">`:>` İşleci hiyerarşisinde yukarı çevirir ve `:?>` işleci hiyerarşinin çevirir.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="8ef6f-152">Yukarı çevrim</span><span class="sxs-lookup"><span data-stu-id="8ef6f-152">Upcasting</span></span>

<span data-ttu-id="8ef6f-153">Birçok nesne odaklı dildeki içinde yukarı çevrim örtük olarak; F #'ta kuralları biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="8ef6f-154">Bir nesne türü yöntemi için değişken geçtiğinizde yukarı çevrim otomatik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="8ef6f-155">Parametre türü esnek bir türü olarak bildirilmiş sürece ancak, Modül içindeki let bağlı işlevler için yukarı çevrim otomatik, değildir.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="8ef6f-156">Daha fazla bilgi için [esnek türler](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="8ef6f-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="8ef6f-157">`:>` İşleç gerçekleştirir statik atama, atama başarılı derleme zamanında belirlenir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="8ef6f-158">Kullanan bir tür dönüştürme, `:>` başarıyla derlenir, geçerli bir yayın olduğunu ve hiçbir şansı çalışma zamanında hata.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="8ef6f-159">Ayrıca `upcast` böyle bir dönüştürme gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="8ef6f-160">Aşağıdaki ifade, hiyerarşi bir dönüştürme belirtir:</span><span class="sxs-lookup"><span data-stu-id="8ef6f-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="8ef6f-161">Upcast işleci kullandığınızda derleyici bağlamdan dönüştürüyorsanız türünün çıkarsanması çalışır.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="8ef6f-162">Derleyicinin hedef türü belirlenemiyor ise, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="8ef6f-163">Alta dönüştürme işlemi</span><span class="sxs-lookup"><span data-stu-id="8ef6f-163">Downcasting</span></span>

<span data-ttu-id="8ef6f-164">`:?>` İşleci gerçekleştiren bir dinamik atama, atama başarılı çalışma zamanında belirlenir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-164">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="8ef6f-165">Kullanan bir yayın `:?>` işleci, derleme zamanında; işaretlenmediği ancak çalışma zamanında girişimini belirtilen türe için yapılır.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-165">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="8ef6f-166">Nesne hedef türüyle uyumlu ise, atama başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-166">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="8ef6f-167">Nesne hedef türüyle uyumlu değil, çalışma zamanı başlatır. bir `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-167">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="8ef6f-168">Ayrıca `downcast` dinamik tür dönüştürmesi gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-168">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="8ef6f-169">Aşağıdaki ifade, hiyerarşide aşağı doğru programı bağlamından çıkarılan bir türe dönüştürmeyi belirtir:</span><span class="sxs-lookup"><span data-stu-id="8ef6f-169">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="8ef6f-170">Olarak `upcast` işleci, derleyici bağlamından belirli hedef türü çıkarımı yapılamıyor, rapor bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-170">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="8ef6f-171">Aşağıdaki kod kullanışını `:>` ve `:?>` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-171">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="8ef6f-172">Kod gösterir `:?>` işleci oluşturur, çünkü dönüştürme başarılı olur olduğunu bildiğiniz durumlarda en iyi şekilde kullanılan `InvalidCastException` dönüştürme başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-172">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="8ef6f-173">Dönüştürme başarılı olur, kullanan bir tür testi bilmiyorsanız bir `match` ifadesi, bir özel durum oluşturma ek yükü önlediği için iyidir.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-173">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="8ef6f-174">Çünkü genel işleçler `downcast` ve `upcast` Yukarıdaki koddaki bağımsız değişkenin ve dönüş türünü belirlemek için tür çıkarımı dayanır, değiştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="8ef6f-174">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="8ef6f-175">örneklerini şununla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="8ef6f-175">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="8ef6f-176">Önceki kodda, bağımsız değişken türü ve dönüş türleri olan `Derived1` ve `Base1`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-176">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="8ef6f-177">Türü testleri hakkında daha fazla bilgi için bkz: [eşleşme ifadeleri](match-Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8ef6f-177">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ef6f-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-178">See also</span></span>

- [<span data-ttu-id="8ef6f-179">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8ef6f-179">F# Language Reference</span></span>](index.md)
