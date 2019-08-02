---
title: İşaretçiden ilgili işleçler- C# başvuru
description: İşaretçilerle C# çalışırken kullanabileceğiniz işleçler hakkında bilgi edinin.
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 830aef8546191df3df4a70e350ba561367a9e474
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512347"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="3b239-103">İşaretçiden ilgili işleçler (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="3b239-103">Pointer related operators (C# reference)</span></span>

<span data-ttu-id="3b239-104">İşaretçilerle çalışmak için aşağıdaki işleçleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3b239-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="3b239-105">[ Birli`&` (Adres-of)](#address-of-operator-) işleci: bir değişkenin adresini almak için</span><span class="sxs-lookup"><span data-stu-id="3b239-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="3b239-106">[ Birli`*` (işaretçi yöneltme)](#pointer-indirection-operator-) işleci: bir işaretçiye işaret eden değişkeni almak için</span><span class="sxs-lookup"><span data-stu-id="3b239-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="3b239-107">(Üye erişimi) ve [ `->` ](#pointer-member-access-operator--) [ `[]` (öğe erişimi)](#pointer-element-access-operator-) işleçleri</span><span class="sxs-lookup"><span data-stu-id="3b239-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="3b239-108">Aritmetik işleçler [ `+` ,`-` ,`++`, ve`--`](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="3b239-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="3b239-109">Karşılaştırma işleçleri [ `==` `!=`, ,`<`,,ve `>` `<=``>=`](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="3b239-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="3b239-110">İşaretçi türleri hakkında bilgi için bkz. [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="3b239-110">For information about pointer types, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3b239-111">İşaretçilerle herhangi bir işlem [güvenli olmayan](../keywords/unsafe.md) bir bağlam gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3b239-111">Any operation with pointers requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="3b239-112">Güvenli olmayan bloklar içeren kodun [`-unsafe`](../compiler-options/unsafe-compiler-option.md) derleyici seçeneğiyle derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b239-112">The code that contains unsafe blocks must be compiled with the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

## <a name="address-of-operator-"></a><span data-ttu-id="3b239-113">Address-of işleci&amp;</span><span class="sxs-lookup"><span data-stu-id="3b239-113">Address-of operator &amp;</span></span>

<span data-ttu-id="3b239-114">Birli `&` işleç, işleneninin adresini döndürür:</span><span class="sxs-lookup"><span data-stu-id="3b239-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

<span data-ttu-id="3b239-115">`&` İşlecin işleneni sabit bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b239-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="3b239-116">*Sabit* değişkenler, [Atık toplayıcısının](../../../standard/garbage-collection/index.md)işleminden etkilenmeyen depolama konumlarında bulunan değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="3b239-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="3b239-117">Yukarıdaki örnekte, yerel değişken `number` yığında bulunduğundan sabit bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="3b239-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="3b239-118">Çöp toplayıcısından etkilenebilecek (örneğin, yeniden konumlandırılan) depolama konumlarında bulunan değişkenler *Taşınabilir* değişkenler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3b239-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="3b239-119">Nesne alanları ve dizi öğeleri taşınabilir değişkenlerin örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="3b239-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="3b239-120">Taşınabilir bir değişkenin adresini, [fixed](../keywords/fixed-statement.md) ifadesiyle "düzeltmenizi" veya "sabitle" yaparsanız alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b239-120">You can get the address of a movable variable if you "fix", or "pin", it with the [fixed](../keywords/fixed-statement.md) statement.</span></span> <span data-ttu-id="3b239-121">Alınan adres yalnızca `fixed` bildiri bloğunun süresi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3b239-121">The obtained address is valid only for the duration of the `fixed` statement block.</span></span> <span data-ttu-id="3b239-122">Aşağıdaki örnek, `fixed` ifadesinin `&` ve işlecinin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="3b239-122">The following example shows how to use the `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="3b239-123">Bir sabit veya bir değerin adresini alamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3b239-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="3b239-124">Sabit ve taşınabilir değişkenler hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sabit ve taşınabilir değişkenler](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3b239-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="3b239-125">Binary `&` işleci, Boolean işlenenlerinin [mantıksal ve](boolean-logical-operators.md#logical-and-operator-) işlecini ya da tam sayı işlenenlerinin [bit düzeyinde mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="3b239-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="3b239-126">İşaretçi yöneltme işleci \*</span><span class="sxs-lookup"><span data-stu-id="3b239-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="3b239-127">Birli işaretçi yöneltme işleci `*` , işleneninin gösterdiği değişkeni edinir.</span><span class="sxs-lookup"><span data-stu-id="3b239-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="3b239-128">Başvuru operatörü olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="3b239-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="3b239-129">`*` İşlecin işleneni bir işaretçi türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b239-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="3b239-130">`*` İşleci türündeki`void*`bir ifadeye uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3b239-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="3b239-131">İkili `*` işleç, sayısal işlenenlerinin [çarpımını](arithmetic-operators.md#multiplication-operator-) hesaplar.</span><span class="sxs-lookup"><span data-stu-id="3b239-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="3b239-132">İşaretçi üyesi erişim işleci-></span><span class="sxs-lookup"><span data-stu-id="3b239-132">Pointer member access operator -></span></span>

<span data-ttu-id="3b239-133">İşleci işaretçi yöneltme ve [üye erişimini](member-access-operators.md#member-access-operator-)birleştirir. [](#pointer-indirection-operator-) `->`</span><span class="sxs-lookup"><span data-stu-id="3b239-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-operator-).</span></span> <span data-ttu-id="3b239-134">Diğer bir deyişle, `x` türü `T*` işaretçisiyse ve `y` ' nin `T`erişilebilir bir üyesi ise, formun bir ifadesi</span><span class="sxs-lookup"><span data-stu-id="3b239-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="3b239-135">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="3b239-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="3b239-136">Aşağıdaki örnek `->` işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="3b239-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="3b239-137">`->` İşleci türündeki`void*`bir ifadeye uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3b239-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="3b239-138">İşaretçi öğesi erişim işleci []</span><span class="sxs-lookup"><span data-stu-id="3b239-138">Pointer element access operator []</span></span>

<span data-ttu-id="3b239-139">İşaretçi türünün bir `p` ifadesi için, formun `p[n]` işaretçi öğesi erişimi olarak `*(p + n)`değerlendirilir; `n` burada `int`, `uint` `long`,, veya ' a örtülü olarak dönüştürülebilir bir tür olması gerekir `ulong`.</span><span class="sxs-lookup"><span data-stu-id="3b239-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="3b239-140">İşaretçilerle `+` işlecin davranışı hakkında daha fazla bilgi için, [bir tam sayı değerinin bir işaretçi bölümüne eklenmesi veya çıkarılması](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3b239-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="3b239-141">Aşağıdaki örnek, bir işaretçi ve `[]` işleçle dizi öğelerine nasıl erişileceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="3b239-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="3b239-142">Örnek, yığındaki bir bellek bloğunu ayırmak için [ `stackalloc` işlecini](stackalloc.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b239-142">The example uses the [`stackalloc` operator](stackalloc.md) to allocate a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="3b239-143">İşaretçi öğesi erişim işleci, sınır dışı hataları denetlemez.</span><span class="sxs-lookup"><span data-stu-id="3b239-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="3b239-144">`[]` Türünde`void*`bir ifadeyle işaretçi öğesi erişimi için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3b239-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="3b239-145">`[]` [Dizi öğesi veya Dizin Oluşturucu erişimi](member-access-operators.md#indexer-operator-)için işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b239-145">You also can use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="3b239-146">İşaretçi aritmetik işleçleri</span><span class="sxs-lookup"><span data-stu-id="3b239-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="3b239-147">İşaretçilerle aşağıdaki aritmetik işlemleri gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3b239-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="3b239-148">Bir işaretçiye veya işaretçiden tamsayı değer ekleme veya çıkarma</span><span class="sxs-lookup"><span data-stu-id="3b239-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="3b239-149">İki işaretçileri çıkar</span><span class="sxs-lookup"><span data-stu-id="3b239-149">Subtract two pointers</span></span>
- <span data-ttu-id="3b239-150">Bir işaretçiyi artırma veya azaltma</span><span class="sxs-lookup"><span data-stu-id="3b239-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="3b239-151">Bu işlemleri türündeki `void*`işaretçilerle gerçekleştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b239-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="3b239-152">Sayısal türlerle desteklenen aritmetik işlemler hakkında daha fazla bilgi için bkz. [Aritmetik işleçler](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="3b239-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="3b239-153">Bir işaretçiye veya bir işaretçiye tamsayı değer ekleme veya çıkarma</span><span class="sxs-lookup"><span data-stu-id="3b239-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="3b239-154">`p` Türünde `long` `int` `n` `uint` `ulong`bir işaretçi ve bir türün bir ifadesi için örtük olarak dönüştürülebilir,,, veya, toplama ve çıkarma için aşağıdaki gibi tanımlanır: `T*`</span><span class="sxs-lookup"><span data-stu-id="3b239-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="3b239-155">Hem `p + n` hem `n + p` de ifadeleri, tarafından `n * sizeof(T)` `T*` verilen`p`adrese eklenmesinin sonucu olan türünde bir işaretçi üretir.</span><span class="sxs-lookup"><span data-stu-id="3b239-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="3b239-156">İfade `p - n` , `n * sizeof(T)` tarafından `T*` verilenadrestençıkarılmasınanedenolantürde`p`bir işaretçi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3b239-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="3b239-157">İşleci bir türün boyutunu bayt cinsinden edinir. [ `sizeof` ](sizeof.md)</span><span class="sxs-lookup"><span data-stu-id="3b239-157">The [`sizeof` operator](sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="3b239-158">Aşağıdaki örnek, bir işaretçi ile `+` işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="3b239-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="3b239-159">İşaretçi çıkarması</span><span class="sxs-lookup"><span data-stu-id="3b239-159">Pointer subtraction</span></span>

<span data-ttu-id="3b239-160">İki `p1` işaretçi ve `p2` türü `T*`için, ifadesi `p1 - p2` tarafından `p1` verilen ve `p2` tarafından bölünenadreslerarasındakifarkıüretir.`sizeof(T)`</span><span class="sxs-lookup"><span data-stu-id="3b239-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="3b239-161">Sonucun `long`türü.</span><span class="sxs-lookup"><span data-stu-id="3b239-161">The type of the result is `long`.</span></span> <span data-ttu-id="3b239-162">Diğer bir deyişle `p1 - p2` , olarak `((long)(p1) - (long)(p2)) / sizeof(T)`hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="3b239-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="3b239-163">Aşağıdaki örnekte işaretçi çıkarma gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3b239-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="3b239-164">İşaretçi artışı ve azaltma</span><span class="sxs-lookup"><span data-stu-id="3b239-164">Pointer increment and decrement</span></span>

<span data-ttu-id="3b239-165">Artış `++` işleci, işaretçi işleneni 1 [ekler](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) .</span><span class="sxs-lookup"><span data-stu-id="3b239-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="3b239-166">Azaltma `--` işleci, 1 işaretçi işlenenden [çıkartır](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) .</span><span class="sxs-lookup"><span data-stu-id="3b239-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="3b239-167">İki tür işleç desteklenir: sonek`p++` (ve `p--`) ve ön ek (`++p` ve `--p`).</span><span class="sxs-lookup"><span data-stu-id="3b239-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="3b239-168">`p++` `p` Ve sonucu`p--` , işlemden *önceki* değeridir.</span><span class="sxs-lookup"><span data-stu-id="3b239-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="3b239-169">`++p` `p` Ve sonucu`--p` , işlemden *sonraki* değeridir.</span><span class="sxs-lookup"><span data-stu-id="3b239-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="3b239-170">Aşağıdaki örnek, hem sonek hem de önek artırma işleçlerinin davranışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="3b239-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="3b239-171">İşaretçi karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="3b239-171">Pointer comparison operators</span></span>

<span data-ttu-id="3b239-172">`==` ,`!=` ,,`>=` , Ve işleçlerini, gibi herhangi bir işaretçi türünün`void*`işlenenlerini karşılaştırmak için kullanabilirsiniz. `<` `>` `<=`</span><span class="sxs-lookup"><span data-stu-id="3b239-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="3b239-173">Bu işleçler, iki işlenen tarafından verilen adresleri işaretsiz tamsayılar gibi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="3b239-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="3b239-174">Diğer türlerin işlenenleri için bu işleçlerin davranışı hakkında daha fazla bilgi için bkz. [eşitlik işleçleri](equality-operators.md) ve [karşılaştırma işleçleri](comparison-operators.md) makaleleri.</span><span class="sxs-lookup"><span data-stu-id="3b239-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="3b239-175">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="3b239-175">Operator precedence</span></span>

<span data-ttu-id="3b239-176">Aşağıdaki liste, işaretçinin ilgili işleçlerini en yüksek öncelikten en düşüğe başlayarak sıralar:</span><span class="sxs-lookup"><span data-stu-id="3b239-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="3b239-177">Sonek artırma `x++` ve azaltma `x--` işleçleri ve `->` ve `[]` işleçleri</span><span class="sxs-lookup"><span data-stu-id="3b239-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="3b239-178">Ön ek `++x` artırma ve `--x` azaltma işleçleri ve `&` ve `*` işleçleri</span><span class="sxs-lookup"><span data-stu-id="3b239-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="3b239-179">Eklenebilir `+` ve `-` işleçler</span><span class="sxs-lookup"><span data-stu-id="3b239-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="3b239-180">Karşılaştırma `<`, `>`, ,`<=`ve işleçler`>=`</span><span class="sxs-lookup"><span data-stu-id="3b239-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="3b239-181">Eşitlik `==` ve `!=` işleçler</span><span class="sxs-lookup"><span data-stu-id="3b239-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="3b239-182">İşleç önceliğine göre `()`uygulanan değerlendirmenin sırasını değiştirmek için parantez ' nu kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b239-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="3b239-183">Öncelik düzeyine göre sıralanan C# işleçlerin tüm listesi için bkz [ C# . işleçler](index.md).</span><span class="sxs-lookup"><span data-stu-id="3b239-183">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="3b239-184">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="3b239-184">Operator overloadability</span></span>

<span data-ttu-id="3b239-185">Kullanıcı tanımlı `&`bir tür, işaretçiyle ilgili işleçleri `->`, `*`, ve ile `[]`aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="3b239-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3b239-186">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3b239-186">C# language specification</span></span>

<span data-ttu-id="3b239-187">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="3b239-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="3b239-188">Sabit ve taşınabilir değişkenler</span><span class="sxs-lookup"><span data-stu-id="3b239-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="3b239-189">Address-of işleci</span><span class="sxs-lookup"><span data-stu-id="3b239-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="3b239-190">İşaretçi yöneltme</span><span class="sxs-lookup"><span data-stu-id="3b239-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="3b239-191">İşaretçi üye erişimi</span><span class="sxs-lookup"><span data-stu-id="3b239-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="3b239-192">İşaretçi öğesi erişimi</span><span class="sxs-lookup"><span data-stu-id="3b239-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="3b239-193">İşaretçi aritmetik</span><span class="sxs-lookup"><span data-stu-id="3b239-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="3b239-194">İşaretçi artışı ve azaltma</span><span class="sxs-lookup"><span data-stu-id="3b239-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="3b239-195">İşaretçi karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="3b239-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="3b239-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b239-196">See also</span></span>

- [<span data-ttu-id="3b239-197">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="3b239-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3b239-198">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="3b239-198">C# operators</span></span>](index.md)
- [<span data-ttu-id="3b239-199">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="3b239-199">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="3b239-200">güvenli olmayan anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="3b239-200">unsafe keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="3b239-201">Fixed anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="3b239-201">fixed keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="3b239-202">stackalloc işleci</span><span class="sxs-lookup"><span data-stu-id="3b239-202">stackalloc operator</span></span>](stackalloc.md)
- [<span data-ttu-id="3b239-203">sizeof işleci</span><span class="sxs-lookup"><span data-stu-id="3b239-203">sizeof operator</span></span>](sizeof.md)
