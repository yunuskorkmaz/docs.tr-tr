---
title: Atama ve Dönüştürmeler
description: F# Programlama dilinin çeşitli temel türler arasında aritmetik dönüştürmeler için dönüştürme işleçleri nasıl sağladığını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: ee4df588caabf58c7b9e18961e217ef8f15fcf93
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630426"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="28421-103">Atama ve Dönüştürmeler (F#)</span><span class="sxs-lookup"><span data-stu-id="28421-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="28421-104">Bu konuda içindeki F#tür dönüştürmeleri için destek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="28421-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="28421-105">Aritmetik türler</span><span class="sxs-lookup"><span data-stu-id="28421-105">Arithmetic Types</span></span>

<span data-ttu-id="28421-106">F#tamsayı ve kayan nokta türleri arasındaki gibi çeşitli temel türler arasında aritmetik dönüştürmeler için dönüştürme işleçleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="28421-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="28421-107">İntegral ve Char dönüştürme işleçleri denetlenen ve Denetlenmemiş formlara sahiptir; kayan nokta işleçleri ve `enum` dönüştürme işleci değildir.</span><span class="sxs-lookup"><span data-stu-id="28421-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="28421-108">Denetlenmemiş Formlar ' de `Microsoft.FSharp.Core.Operators` tanımlanmıştır ve denetlenen formlarda ' de `Microsoft.FSharp.Core.Operators.Checked`tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="28421-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="28421-109">Denetlenen formlar taşma durumunu denetler ve elde edilen değer hedef türün sınırlarını aşarsa bir çalışma zamanı özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="28421-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="28421-110">Bu işleçlerin her biri, hedef türünün adı ile aynı ada sahiptir.</span><span class="sxs-lookup"><span data-stu-id="28421-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="28421-111">Örneğin, aşağıdaki kodda, türlerin açıkça açıklandığı `byte` , iki farklı anlam ile görünür.</span><span class="sxs-lookup"><span data-stu-id="28421-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="28421-112">İlk oluşum türdür, ikincisi ise dönüştürme işleçtir.</span><span class="sxs-lookup"><span data-stu-id="28421-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="28421-113">Aşağıdaki tabloda ' de F#tanımlanan dönüştürme işleçleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="28421-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="28421-114">İşleç</span><span class="sxs-lookup"><span data-stu-id="28421-114">Operator</span></span>|<span data-ttu-id="28421-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28421-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="28421-116">8 bit işaretsiz bir tür bayta Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="28421-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="28421-117">İşaretli bayta Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="28421-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="28421-118">16 bit işaretli tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="28421-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="28421-119">16 bit işaretsiz tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="28421-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="28421-120">32 bitlik işaretli tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="28421-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="28421-121">32 bitlik işaretsiz tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="28421-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="28421-122">64 bitlik işaretli tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="28421-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="28421-123">64 bitlik işaretsiz tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="28421-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="28421-124">Yerel tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="28421-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="28421-125">İşaretsiz yerel tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="28421-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="28421-126">64 bitlik bir çift duyarlıklı IEEE kayan noktalı sayıya dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="28421-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="28421-127">32 bitlik tek duyarlıklı bir IEEE kayan noktalı sayıya dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="28421-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="28421-128">Öğesine `System.Decimal`Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="28421-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="28421-129">`System.Char`Unicode karaktere Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="28421-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="28421-130">Numaralandırılmış bir türe Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="28421-130">Convert to an enumerated type.</span></span>|

<span data-ttu-id="28421-131">Yerleşik temel türlerin yanı sıra, bu işleçleri, veya `op_Explicit` `op_Implicit` uygun imzalara sahip Yöntemler uygulayan türlerle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28421-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="28421-132">Örneğin, `int` dönüştürme işleci, türü parametre olarak alan ve döndüren `int`statik bir yöntem `op_Explicit` sağlayan herhangi bir tür ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28421-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="28421-133">Genel kurala özel bir özel durum olarak, metotları dönüş türü tarafından aşırı yüklenemez, ve `op_Explicit` `op_Implicit`için bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28421-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="28421-134">Numaralandırılmış türler</span><span class="sxs-lookup"><span data-stu-id="28421-134">Enumerated Types</span></span>

<span data-ttu-id="28421-135">İşleci, dönüştürülecek `enum` öğesinin türünü temsil eden bir tür parametresi alan genel bir işleçtir. `enum`</span><span class="sxs-lookup"><span data-stu-id="28421-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="28421-136">Numaralandırılmış bir türe dönüşürse, dönüştürmek istediğiniz öğesinin `enum` türünü belirlemekte çıkarım denemeleri yazın.</span><span class="sxs-lookup"><span data-stu-id="28421-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="28421-137">Aşağıdaki örnekte, değişkeni `col1` açıkça açıklama eklenmiş değildir, ancak türü daha sonraki eşitlik testinde çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="28421-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="28421-138">Bu nedenle, derleyici bir `Color` numaralandırmaya dönüştürmekte olduğunuz tarafından ortaya çıkarılamıyor.</span><span class="sxs-lookup"><span data-stu-id="28421-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="28421-139">Alternatif olarak, aşağıdaki örnekte olduğu gibi `col2` bir tür ek açıklaması sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28421-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

<span data-ttu-id="28421-140">Hedef numaralandırma türünü, aşağıdaki kodda olduğu gibi açıkça bir tür parametresi olarak da belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="28421-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="28421-141">Sabit listesinin, yalnızca Numaralandırmadaki temeldeki tür, dönüştürülmekte olan türle uyumluysa çalıştığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="28421-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="28421-142">Aşağıdaki kodda, ve `int32` `uint32`arasındaki uyuşmazlığın nedeniyle dönüştürme derlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="28421-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="28421-143">Daha fazla bilgi için bkz. [numaralandırmalar](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="28421-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="28421-144">Nesne türlerini atama</span><span class="sxs-lookup"><span data-stu-id="28421-144">Casting Object Types</span></span>

<span data-ttu-id="28421-145">Nesne hiyerarşisindeki türler arasında dönüştürme, nesne odaklı programlama için temel bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="28421-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="28421-146">İki temel dönüştürme türü vardır: atama (yukarı atama) ve (aşağı atama).</span><span class="sxs-lookup"><span data-stu-id="28421-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="28421-147">Bir hiyerarşiyi atama, türetilmiş bir nesne başvurusundan bir temel nesne başvurusuna atama anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="28421-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="28421-148">Bu tür bir dönüştürme, temel sınıf türetilmiş sınıfın devralma hiyerarşisinde olduğu sürece çalışma garantisi verir.</span><span class="sxs-lookup"><span data-stu-id="28421-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="28421-149">Bir hiyerarşiyi, bir temel nesne başvurusundan türetilmiş bir nesne başvurusuna dönüştürme işlemi, yalnızca nesne doğru hedef (türetilen) türünün bir örneği veya hedef türünden türetilmiş bir tür olduğunda başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="28421-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="28421-150">F#Bu dönüştürme türleri için işleçler sağlar.</span><span class="sxs-lookup"><span data-stu-id="28421-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="28421-151">İşleci hiyerarşiyi yayınlar `:?>` ve operatör hiyerarşiyi aşağı yayınlar. `:>`</span><span class="sxs-lookup"><span data-stu-id="28421-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="28421-152">Yukarı atama</span><span class="sxs-lookup"><span data-stu-id="28421-152">Upcasting</span></span>

<span data-ttu-id="28421-153">Birçok nesne yönelimli dilde, yukarı atama örtük bir şekilde; ' F#de, kurallar biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="28421-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="28421-154">Bağımsız değişkenleri bir nesne türündeki yöntemlere geçirdiğinizde, upatama otomatik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="28421-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="28421-155">Ancak, bir modüldeki izin-sınırlı işlevler için, parametre türü esnek bir tür olarak bildirilemediği sürece, UPI otomatik değildir.</span><span class="sxs-lookup"><span data-stu-id="28421-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="28421-156">Daha fazla bilgi için bkz. [Esnek türler](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="28421-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="28421-157">`:>` İşleci statik bir atama gerçekleştirir, bu, dönüştürmenin başarısı derleme zamanında belirlendiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="28421-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="28421-158">Kullanan `:>` bir tür başarıyla derleniyorsa, bu geçerli bir tür ve çalışma zamanında hata şansı yoktur.</span><span class="sxs-lookup"><span data-stu-id="28421-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="28421-159">Bu tür bir dönüştürme gerçekleştirmek `upcast` için işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28421-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="28421-160">Aşağıdaki ifade hiyerarşinin bir dönüşümünü belirtir:</span><span class="sxs-lookup"><span data-stu-id="28421-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="28421-161">Upcast işlecini kullandığınızda, derleyici, bağlamındaki dönüştürmekte olduğunuz türü çıkarmakta çalışır.</span><span class="sxs-lookup"><span data-stu-id="28421-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="28421-162">Derleyici hedef türünü tespit leyemiyorsa, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="28421-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="28421-163">Alta çevrim</span><span class="sxs-lookup"><span data-stu-id="28421-163">Downcasting</span></span>

<span data-ttu-id="28421-164">`:?>` İşleci dinamik bir atama gerçekleştirir, bu, dönüştürmenin başarısı çalışma zamanında belirlendiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="28421-164">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="28421-165">`:?>` İşleci kullanan bir tür derleme zamanında denetlenmez; ancak çalışma zamanında, belirtilen türe atama için bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="28421-165">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="28421-166">Nesne hedef türle uyumluysa, atama başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="28421-166">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="28421-167">Nesne hedef türle uyumlu değilse, çalışma zamanı bir `InvalidCastException`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="28421-167">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="28421-168">Dinamik bir tür dönüştürmesi gerçekleştirmek `downcast` için işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28421-168">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="28421-169">Aşağıdaki ifade, hiyerarşinin bir program bağlamından çıkarılan bir türe dönüştürülmesini belirtir:</span><span class="sxs-lookup"><span data-stu-id="28421-169">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="28421-170">`upcast` İşleci olarak, derleyici bağlamdan belirli bir hedef türü çıkarsanamıyor bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="28421-170">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="28421-171">Aşağıdaki kod, `:>` ve `:?>` işleçlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28421-171">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="28421-172">Kod, dönüştürmenin başarılı `:?>` `InvalidCastException` olacağını bildiğiniz zaman, dönüştürmenin başarısız olup olmadığını belirten işlecin en iyi şekilde kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28421-172">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="28421-173">Dönüştürmenin başarılı olacağını görmüyorsanız, bir `match` ifade kullanan bir tür testi daha iyidir, çünkü özel durum oluşturma ek yükünü önler.</span><span class="sxs-lookup"><span data-stu-id="28421-173">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="28421-174">Bağımsız değişkeni ve `downcast` dönüş `upcast` türünü belirleyebilmek için genel işleçler ve tür çıkarımı kullandığından, yukarıdaki kodda değiştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="28421-174">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="28421-175">örneklerini şununla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="28421-175">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="28421-176">Önceki kodda, bağımsız değişken türü ve dönüş türleri sırasıyla ve `Derived1` `Base1`' dir.</span><span class="sxs-lookup"><span data-stu-id="28421-176">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="28421-177">Tür testleri hakkında daha fazla bilgi için bkz. [Match ifadeleri](match-Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="28421-177">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="28421-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28421-178">See also</span></span>

- [<span data-ttu-id="28421-179">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="28421-179">F# Language Reference</span></span>](index.md)
