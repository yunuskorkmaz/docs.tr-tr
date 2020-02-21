---
title: Atama ve Dönüştürmeler
description: F# Programlama dilinin çeşitli temel türler arasında aritmetik dönüştürmeler için dönüştürme işleçleri nasıl sağladığını öğrenin.
ms.date: 02/20/2020
ms.openlocfilehash: 5f9727d14a7ae070e0f0f71fa0a0abe04f662071
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543592"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="507c9-103">Atama ve Dönüştürmeler (F#)</span><span class="sxs-lookup"><span data-stu-id="507c9-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="507c9-104">Bu konuda içindeki F#tür dönüştürmeleri için destek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="507c9-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="507c9-105">Aritmetik türler</span><span class="sxs-lookup"><span data-stu-id="507c9-105">Arithmetic Types</span></span>

<span data-ttu-id="507c9-106">F#tamsayı ve kayan nokta türleri arasındaki gibi çeşitli temel türler arasında aritmetik dönüştürmeler için dönüştürme işleçleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="507c9-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="507c9-107">İntegral ve Char dönüştürme işleçleri denetlenen ve Denetlenmemiş formlara sahiptir; kayan nokta işleçleri ve `enum` dönüştürme işleci değildir.</span><span class="sxs-lookup"><span data-stu-id="507c9-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="507c9-108">Denetlenmemiş formlar `Microsoft.FSharp.Core.Operators` tanımlanmıştır ve denetlenen formlar `Microsoft.FSharp.Core.Operators.Checked`tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="507c9-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="507c9-109">Denetlenen formlar taşma durumunu denetler ve elde edilen değer hedef türün sınırlarını aşarsa bir çalışma zamanı özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="507c9-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="507c9-110">Bu işleçlerin her biri, hedef türünün adı ile aynı ada sahiptir.</span><span class="sxs-lookup"><span data-stu-id="507c9-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="507c9-111">Örneğin, aşağıdaki kodda, türlerin açıkça açıklandığı, `byte` iki farklı anlam ile görünür.</span><span class="sxs-lookup"><span data-stu-id="507c9-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="507c9-112">İlk oluşum türdür, ikincisi ise dönüştürme işleçtir.</span><span class="sxs-lookup"><span data-stu-id="507c9-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="507c9-113">Aşağıdaki tabloda ' de F#tanımlanan dönüştürme işleçleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="507c9-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="507c9-114">İşleç</span><span class="sxs-lookup"><span data-stu-id="507c9-114">Operator</span></span>|<span data-ttu-id="507c9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="507c9-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="507c9-116">8 bit işaretsiz bir tür bayta Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="507c9-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="507c9-117">İşaretli bayta Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="507c9-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="507c9-118">16 bit işaretli tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="507c9-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="507c9-119">16 bit işaretsiz tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="507c9-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="507c9-120">32 bitlik işaretli tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="507c9-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="507c9-121">32 bitlik işaretsiz tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="507c9-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="507c9-122">64 bitlik işaretli tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="507c9-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="507c9-123">64 bitlik işaretsiz tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="507c9-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="507c9-124">Yerel tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="507c9-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="507c9-125">İşaretsiz yerel tamsayıya Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="507c9-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="507c9-126">64 bitlik bir çift duyarlıklı IEEE kayan noktalı sayıya dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="507c9-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="507c9-127">32 bitlik tek duyarlıklı bir IEEE kayan noktalı sayıya dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="507c9-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="507c9-128">`System.Decimal`Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="507c9-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="507c9-129">Bir Unicode karakter olan `System.Char`Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="507c9-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="507c9-130">Numaralandırılmış bir türe Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="507c9-130">Convert to an enumerated type.</span></span>|

<span data-ttu-id="507c9-131">Yerleşik temel türlerin yanı sıra, bu işleçleri, uygun imzalara sahip `op_Explicit` veya `op_Implicit` Yöntemler uygulayan türlerle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="507c9-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="507c9-132">Örneğin, `int` dönüştürme işleci, türü parametre olarak alan ve `int`döndüren statik bir yöntem `op_Explicit` sağlayan herhangi bir tür ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="507c9-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="507c9-133">Genel kurala özel bir özel durum olarak, metotları dönüş türü tarafından aşırı yüklenemez, bunu `op_Explicit` ve `op_Implicit`için yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="507c9-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="507c9-134">Numaralandırılmış türler</span><span class="sxs-lookup"><span data-stu-id="507c9-134">Enumerated Types</span></span>

<span data-ttu-id="507c9-135">`enum` işleci, dönüştürülecek `enum` türünü temsil eden bir tür parametresi alan genel bir işleçtir.</span><span class="sxs-lookup"><span data-stu-id="507c9-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="507c9-136">Numaralandırılmış bir türe dönüşürse, dönüştürmek istediğiniz `enum` türünü tespit etmek için çıkarım denemeleri yazın.</span><span class="sxs-lookup"><span data-stu-id="507c9-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="507c9-137">Aşağıdaki örnekte `col1` değişkeni açıkça açıklanmaz, ancak türü daha sonraki eşitlik testinde çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="507c9-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="507c9-138">Bu nedenle, derleyici `Color` bir numaralandırmaya dönüştürmekte olduğunuz tarafından ortaya çıkarılamıyor.</span><span class="sxs-lookup"><span data-stu-id="507c9-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="507c9-139">Alternatif olarak, aşağıdaki örnekte `col2` gibi bir tür ek açıklaması sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="507c9-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

<span data-ttu-id="507c9-140">Hedef numaralandırma türünü, aşağıdaki kodda olduğu gibi açıkça bir tür parametresi olarak da belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="507c9-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="507c9-141">Sabit listesinin, yalnızca Numaralandırmadaki temeldeki tür, dönüştürülmekte olan türle uyumluysa çalıştığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="507c9-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="507c9-142">Aşağıdaki kodda, `int32` ve `uint32`arasındaki uyuşmazlık nedeniyle dönüştürme derlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="507c9-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="507c9-143">Daha fazla bilgi için bkz. [numaralandırmalar](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="507c9-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="507c9-144">Nesne türlerini atama</span><span class="sxs-lookup"><span data-stu-id="507c9-144">Casting Object Types</span></span>

<span data-ttu-id="507c9-145">Nesne hiyerarşisindeki türler arasında dönüştürme, nesne odaklı programlama için temel bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="507c9-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="507c9-146">İki temel dönüştürme türü vardır: atama (yukarı atama) ve (aşağı atama).</span><span class="sxs-lookup"><span data-stu-id="507c9-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="507c9-147">Bir hiyerarşiyi atama, türetilmiş bir nesne başvurusundan bir temel nesne başvurusuna atama anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="507c9-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="507c9-148">Bu tür bir dönüştürme, temel sınıf türetilmiş sınıfın devralma hiyerarşisinde olduğu sürece çalışma garantisi verir.</span><span class="sxs-lookup"><span data-stu-id="507c9-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="507c9-149">Bir hiyerarşiyi, bir temel nesne başvurusundan türetilmiş bir nesne başvurusuna dönüştürme işlemi, yalnızca nesne doğru hedef (türetilen) türünün bir örneği veya hedef türünden türetilmiş bir tür olduğunda başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="507c9-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="507c9-150">F#Bu dönüştürme türleri için işleçler sağlar.</span><span class="sxs-lookup"><span data-stu-id="507c9-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="507c9-151">`:>` işleci hiyerarşiyi yayınlar ve `:?>` işleci hiyerarşiyi aşağı yayınlar.</span><span class="sxs-lookup"><span data-stu-id="507c9-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="507c9-152">Yukarı atama</span><span class="sxs-lookup"><span data-stu-id="507c9-152">Upcasting</span></span>

<span data-ttu-id="507c9-153">Birçok nesne yönelimli dilde, yukarı atama örtük bir şekilde; ' F#de, kurallar biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="507c9-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="507c9-154">Bağımsız değişkenleri bir nesne türündeki yöntemlere geçirdiğinizde, upatama otomatik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="507c9-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="507c9-155">Ancak, bir modüldeki izin-sınırlı işlevler için, parametre türü esnek bir tür olarak bildirilemediği sürece, UPI otomatik değildir.</span><span class="sxs-lookup"><span data-stu-id="507c9-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="507c9-156">Daha fazla bilgi için bkz. [Esnek türler](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="507c9-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="507c9-157">`:>` işleci statik bir atama gerçekleştirir, bu, dönüştürmenin başarısı derleme zamanında belirlendiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="507c9-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="507c9-158">`:>` kullanan bir tür başarıyla derleniyorsa, bu geçerli bir tür ve çalışma zamanında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="507c9-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="507c9-159">Bu tür bir dönüştürme gerçekleştirmek için `upcast` işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="507c9-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="507c9-160">Aşağıdaki ifade hiyerarşinin bir dönüşümünü belirtir:</span><span class="sxs-lookup"><span data-stu-id="507c9-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="507c9-161">Upcast işlecini kullandığınızda, derleyici, bağlamındaki dönüştürmekte olduğunuz türü çıkarmakta çalışır.</span><span class="sxs-lookup"><span data-stu-id="507c9-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="507c9-162">Derleyici hedef türünü tespit leyemiyorsa, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="507c9-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span> <span data-ttu-id="507c9-163">Tür ek açıklaması gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="507c9-163">A type annotation may be required.</span></span>

### <a name="downcasting"></a><span data-ttu-id="507c9-164">Alta çevrim</span><span class="sxs-lookup"><span data-stu-id="507c9-164">Downcasting</span></span>

<span data-ttu-id="507c9-165">`:?>` işleci dinamik bir atama gerçekleştirir, bu, dönüştürmenin başarısı çalışma zamanında belirlendiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="507c9-165">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="507c9-166">`:?>` işlecini kullanan bir tür derleme sırasında denetlenmez; Ancak çalışma zamanında, belirtilen türe dönüştürmek için bir girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="507c9-166">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="507c9-167">Nesne hedef türle uyumluysa, atama başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="507c9-167">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="507c9-168">Nesne hedef türle uyumlu değilse, çalışma zamanı bir `InvalidCastException`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="507c9-168">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="507c9-169">Dinamik bir tür dönüştürmesi gerçekleştirmek için `downcast` işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="507c9-169">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="507c9-170">Aşağıdaki ifade, hiyerarşinin bir program bağlamından çıkarılan bir türe dönüştürülmesini belirtir:</span><span class="sxs-lookup"><span data-stu-id="507c9-170">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="507c9-171">`upcast` işleci olarak, derleyici bağlamdan belirli bir hedef türü çıkarsanamıyor bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="507c9-171">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span> <span data-ttu-id="507c9-172">Tür ek açıklaması gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="507c9-172">A type annotation may be required.</span></span>

<span data-ttu-id="507c9-173">Aşağıdaki kod `:>` ve `:?>` işleçlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="507c9-173">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="507c9-174">Kod, dönüştürmenin başarılı olacağını bildiğiniz için `:?>` işlecinin en iyi kullanıldığını gösterir, çünkü dönüştürme başarısız olursa `InvalidCastException` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="507c9-174">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="507c9-175">Dönüştürmenin başarılı olacağını görmüyorsanız, bir özel durum oluşturma yükünü önlediği için `match` ifadesi kullanan bir tür testi daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="507c9-175">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="507c9-176">Genel işleçler `downcast` ve `upcast` bağımsız değişkeni ve dönüş türünü belirleyebilmek için tür çıkarımı kullandığından, yukarıdaki kodda değiştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="507c9-176">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="507c9-177">şununla değiştirin</span><span class="sxs-lookup"><span data-stu-id="507c9-177">with</span></span>

```fsharp
let base1: Base1 = upcast d1
```

<span data-ttu-id="507c9-178">Bir tür ek açıklaması gerektiğini unutmayın, çünkü kendisi `upcast`, temel sınıfı belirleyemez.</span><span class="sxs-lookup"><span data-stu-id="507c9-178">Note that a type annotation is required, since `upcast` by itself could not determine the base class.</span></span>

## <a name="see-also"></a><span data-ttu-id="507c9-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="507c9-179">See also</span></span>

- [<span data-ttu-id="507c9-180">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="507c9-180">F# Language Reference</span></span>](index.md)
