---
title: İşaretçi işleçleri - ilgili C# başvurusu
description: Hakkında bilgi edinin C# işaretçilerle çalışırken kullanabileceğiniz işleçleri.
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
ms.openlocfilehash: 0cc104c7246763ee32866fe5233b9774253a2888
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833133"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="91542-103">İşaretçi ilgili işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="91542-103">Pointer related operators (C# Reference)</span></span>

<span data-ttu-id="91542-104">İşaretçiler ile çalışmak için aşağıdaki işleçleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="91542-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="91542-105">Birli [ `&` (adres-of)](#address-of-operator-) işleci: değişkenin adresini almak için</span><span class="sxs-lookup"><span data-stu-id="91542-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="91542-106">Birli [ `*` (işaretçi yöneltmesi)](#pointer-indirection-operator-) işleci: işaretçi tarafından işaret edilen değişkeni almak için</span><span class="sxs-lookup"><span data-stu-id="91542-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="91542-107">[ `->` (Üye erişimi)](#pointer-member-access-operator--) ve [ `[]` (öğe erişimi)](#pointer-element-access-operator-) işleçleri</span><span class="sxs-lookup"><span data-stu-id="91542-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="91542-108">Aritmetik işleçler [ `+`, `-`, `++`, ve `--`](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="91542-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="91542-109">Karşılaştırma işleçleri [ `==`, `!=`, `<`, `>`, `<=`, ve `>=`](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="91542-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="91542-110">İşaretçi türleri hakkında daha fazla bilgi için bkz. [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="91542-110">For information about pointer types, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

> [!NOTE]
> <span data-ttu-id="91542-111">İşaretçiler içeren herhangi bir işlem gerektiren bir [güvenli](../keywords/unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="91542-111">Any operation with pointers requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="91542-112">Güvenli olmayan bloklar içeren kod ile derlenmelidir [ `-unsafe` ](../compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="91542-112">The code that contains unsafe blocks must be compiled with the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

## <a name="address-of-operator-amp"></a><span data-ttu-id="91542-113">Address-of işleci &amp;</span><span class="sxs-lookup"><span data-stu-id="91542-113">Address-of operator &amp;</span></span>

<span data-ttu-id="91542-114">Birli `&` işleci, işlenenin adresini verir:</span><span class="sxs-lookup"><span data-stu-id="91542-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

<span data-ttu-id="91542-115">İşleneni `&` işleci, sabit bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91542-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="91542-116">*Sabit* değişkenlerdir bir işlem tarafından etkilenmez, depolama konumları bulunan değişkenleri [çöp toplayıcı](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="91542-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="91542-117">Yukarıdaki örnekte, yerel değişken `number` yığında yer aldığından bir sabit değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="91542-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="91542-118">Atık toplayıcı (örneğin, yeniden konumlandırılması) etkilenen depolama konumları bulunan değişkenleri çağrılır *taşınabilir* değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="91542-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="91542-119">Nesne alanları ve dizi öğeleri taşınabilir değişkenleri örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="91542-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="91542-120">"Düzeltme" veya "sabitleme" taşınabilir değişkenin adresini alabilirsiniz ile [sabit](../keywords/fixed-statement.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="91542-120">You can get the address of a movable variable if you "fix", or "pin", it with the [fixed](../keywords/fixed-statement.md) statement.</span></span> <span data-ttu-id="91542-121">Alınan adresi süresi boyunca yalnızca geçerli `fixed` deyim bloğu.</span><span class="sxs-lookup"><span data-stu-id="91542-121">The obtained address is valid only for the duration of the `fixed` statement block.</span></span> <span data-ttu-id="91542-122">Aşağıdaki örnek nasıl kullanılacağını gösterir `fixed` deyimi ve `&` işleci:</span><span class="sxs-lookup"><span data-stu-id="91542-122">The following example shows how to use the `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="91542-123">Bir sabit bir değer veya adresi alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="91542-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="91542-124">Sabit ve taşınabilir değişkenleri hakkında daha fazla bilgi için bkz. [sabit ve taşınabilir değişkenleri](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="91542-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="91542-125">İkili `&` işleci hesaplar [mantıksal AND](boolean-logical-operators.md#logical-and-operator-) Boole işlenenleri, veya [mantıksal bit düzeyinde AND](bitwise-and-shift-operators.md#logical-and-operator-) integral işlenenleri biri.</span><span class="sxs-lookup"><span data-stu-id="91542-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="91542-126">İşaretçi yöneltme işleci \*</span><span class="sxs-lookup"><span data-stu-id="91542-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="91542-127">İşaretçi yöneltme işleci birli `*` işlenenin işaret ettiği değişken alır.</span><span class="sxs-lookup"><span data-stu-id="91542-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="91542-128">Başvuru işleci olarak da bilinen olduğu.</span><span class="sxs-lookup"><span data-stu-id="91542-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="91542-129">İşleneni `*` işleci, bir işaretçi türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91542-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="91542-130">Uygulayamazsınız `*` türündeki bir ifade işlecine `void*`.</span><span class="sxs-lookup"><span data-stu-id="91542-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="91542-131">İkili `*` işleci hesaplar [ürün](arithmetic-operators.md#multiplication-operator-) sayısal işlenenleri biri.</span><span class="sxs-lookup"><span data-stu-id="91542-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="91542-132">İşaretçi üye erişimi işleci ' -></span><span class="sxs-lookup"><span data-stu-id="91542-132">Pointer member access operator -></span></span>

<span data-ttu-id="91542-133">`->` İşleci birleştirir [işaretçi yöneltmesi](#pointer-indirection-operator-) ve [üye erişimi](member-access-operators.md#member-access-operator-).</span><span class="sxs-lookup"><span data-stu-id="91542-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-operator-).</span></span> <span data-ttu-id="91542-134">Diğer bir deyişle, `x` bir işaretçi türü `T*` ve `y` erişilebilir bir üyesidir `T`, formun bir ifade</span><span class="sxs-lookup"><span data-stu-id="91542-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="91542-135">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="91542-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="91542-136">Aşağıdaki örnek, kullanımını gösterir. `->` işleci:</span><span class="sxs-lookup"><span data-stu-id="91542-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="91542-137">Uygulayamazsınız `->` türündeki bir ifade işlecine `void*`.</span><span class="sxs-lookup"><span data-stu-id="91542-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="91542-138">İşaretçi öğesi erişim operator]</span><span class="sxs-lookup"><span data-stu-id="91542-138">Pointer element access operator []</span></span>

<span data-ttu-id="91542-139">Bir ifade için `p` bir işaretçi türü, bir işaretçiyi öğe erişimi formun `p[n]` olarak değerlendirilir `*(p + n)`burada `n` örtük olarak dönüştürülebilir türde olmalıdır `int`, `uint`, `long`, veya `ulong`.</span><span class="sxs-lookup"><span data-stu-id="91542-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="91542-140">Davranışı hakkında bilgi için `+` işaretçisi olan işleç bkz [ekleme veya çıkarma, bir tamsayı değeri ya da bir işaretçiden](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) bölümü.</span><span class="sxs-lookup"><span data-stu-id="91542-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="91542-141">Aşağıdaki örnek, bir işaretçi ile dizi öğelerini nasıl erişileceğini gösteren ve `[]` işleci:</span><span class="sxs-lookup"><span data-stu-id="91542-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="91542-142">Örnekte [ `stackalloc` işleci](stackalloc.md) bir yığında bellek bloğu ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="91542-142">The example uses the [`stackalloc` operator](stackalloc.md) to allocate a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="91542-143">İşaretçi öğesi erişim işleci için işlemleri denetlemez hataları.</span><span class="sxs-lookup"><span data-stu-id="91542-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="91542-144">Kullanamazsınız `[]` işaretçi türündeki bir ifade ile öğesi erişim için `void*`.</span><span class="sxs-lookup"><span data-stu-id="91542-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="91542-145">Ayrıca `[]` işleci için [dizi öğesi veya dizin oluşturucu erişim](member-access-operators.md#indexer-operator-).</span><span class="sxs-lookup"><span data-stu-id="91542-145">You also can use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="91542-146">İşaretçi aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="91542-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="91542-147">İşaretçiler ile aşağıdaki aritmetik işlemleri gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="91542-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="91542-148">Eklemek veya çıkarmak için veya işaretçiden bir tamsayı değeri</span><span class="sxs-lookup"><span data-stu-id="91542-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="91542-149">İki işaretçi çıkarma</span><span class="sxs-lookup"><span data-stu-id="91542-149">Subtract two pointers</span></span>
- <span data-ttu-id="91542-150">Artırma veya azaltma bir işaretçi</span><span class="sxs-lookup"><span data-stu-id="91542-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="91542-151">Türü işaretçileri olan işlemleri gerçekleştiremezsiniz `void*`.</span><span class="sxs-lookup"><span data-stu-id="91542-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="91542-152">Sayısal türler ile desteklenen aritmetik işlemler hakkında daha fazla bilgi için bkz. [aritmetik işleçler](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="91542-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="91542-153">Toplama veya bir tamsayı değeri ya da bir işaretçiden çıkarma</span><span class="sxs-lookup"><span data-stu-id="91542-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="91542-154">İşaretçisi `p` türü `T*` ve ifade `n` örtük olarak dönüştürülebilir bir türün `int`, `uint`, `long`, veya `ulong`, toplama ve çıkarma tanımlandığı gibi:</span><span class="sxs-lookup"><span data-stu-id="91542-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="91542-155">Her ikisi de `p + n` ve `n + p` ifadeler üretmek türünde bir işaretçi `T*` sonuçlarının eklemesini `n * sizeof(T)` tarafından verilen adresine `p`.</span><span class="sxs-lookup"><span data-stu-id="91542-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="91542-156">`p - n` Türünde bir işaretçi ifadesi oluşturur `T*` sonuçlarının arasındaki çıkarma işleminin `n * sizeof(T)` tarafından verilen adresinden `p`.</span><span class="sxs-lookup"><span data-stu-id="91542-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="91542-157">[ `sizeof` İşleci](../keywords/sizeof.md) bir tür bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="91542-157">The [`sizeof` operator](../keywords/sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="91542-158">Aşağıdaki örnek, kullanımını gösterir. `+` işleci bir işaretçi ile:</span><span class="sxs-lookup"><span data-stu-id="91542-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="91542-159">İşaretçi çıkarması</span><span class="sxs-lookup"><span data-stu-id="91542-159">Pointer subtraction</span></span>

<span data-ttu-id="91542-160">İki işaretçileri `p1` ve `p2` türü `T*`, ifade `p1 - p2` tarafından verilen adresler arasındaki farkı verir `p1` ve `p2` bölü `sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="91542-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="91542-161">Sonuç türü olan `long`.</span><span class="sxs-lookup"><span data-stu-id="91542-161">The type of the result is `long`.</span></span> <span data-ttu-id="91542-162">Diğer bir deyişle, `p1 - p2` olarak hesaplanan `((long)(p1) - (long)(p2)) / sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="91542-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="91542-163">Aşağıdaki örnek, işaretçi çıkarması gösterir:</span><span class="sxs-lookup"><span data-stu-id="91542-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="91542-164">İşaretçi artırma ve azaltma</span><span class="sxs-lookup"><span data-stu-id="91542-164">Pointer increment and decrement</span></span>

<span data-ttu-id="91542-165">`++` Artış işleci [ekler](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) işaretçi işleneniyle 1.</span><span class="sxs-lookup"><span data-stu-id="91542-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="91542-166">`--` Azaltma işleci [çıkarır](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) işaretçi işleneniyle 1.</span><span class="sxs-lookup"><span data-stu-id="91542-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="91542-167">Her iki işleçler iki biçimde desteklenir: sonek (`p++` ve `p--`) ve önek (`++p` ve `--p`).</span><span class="sxs-lookup"><span data-stu-id="91542-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="91542-168">Sonucu `p++` ve `p--` değeri `p` *önce* işlemi.</span><span class="sxs-lookup"><span data-stu-id="91542-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="91542-169">Sonucu `++p` ve `--p` değeri `p` *sonra* işlemi.</span><span class="sxs-lookup"><span data-stu-id="91542-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="91542-170">Aşağıdaki örnek, sonek hem önek artırma işleçleri davranışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="91542-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="91542-171">İşaretçi Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="91542-171">Pointer comparison operators</span></span>

<span data-ttu-id="91542-172">Kullanabileceğiniz `==`, `!=`, `<`, `>`, `<=`, ve `>=` işlenen bir işaretçi türünü karşılaştırmak için işleçleri dahil olmak üzere `void*`.</span><span class="sxs-lookup"><span data-stu-id="91542-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="91542-173">Bu işleçler, işaretsiz tamsayılar değilmiş gibi iki işlenen tarafından belirtilen adresi karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="91542-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="91542-174">Bu işleçler diğer türündeki işlenenler için davranış hakkında daha fazla bilgi için bkz. [eşitlik işleçleri](equality-operators.md) ve [Karşılaştırma işleçleri](comparison-operators.md) makaleler.</span><span class="sxs-lookup"><span data-stu-id="91542-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="91542-175">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="91542-175">Operator precedence</span></span>

<span data-ttu-id="91542-176">Aşağıdaki liste siparişler işaretçi işleçleri en yüksek öncelikten en düşük başlangıç ilgili:</span><span class="sxs-lookup"><span data-stu-id="91542-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="91542-177">Sonek artırma `x++` ve azaltma `x--` işleçler ve `->` ve `[]` işleçleri</span><span class="sxs-lookup"><span data-stu-id="91542-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="91542-178">Önek artırma `++x` ve azaltma `--x` işleçler ve `&` ve `*` işleçleri</span><span class="sxs-lookup"><span data-stu-id="91542-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="91542-179">Eklenebilir `+` ve `-` işleçleri</span><span class="sxs-lookup"><span data-stu-id="91542-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="91542-180">Karşılaştırma `<`, `>`, `<=`, ve `>=` işleçleri</span><span class="sxs-lookup"><span data-stu-id="91542-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="91542-181">Eşitlik `==` ve `!=` işleçleri</span><span class="sxs-lookup"><span data-stu-id="91542-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="91542-182">Parantez kullanın `()`İşleç önceliği tarafından belirlenen değerlendirmenin sırasını değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="91542-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="91542-183">Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="91542-183">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="91542-184">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="91542-184">Operator overloadability</span></span>

<span data-ttu-id="91542-185">Kullanıcı tanımlı bir tür işaretçisi aşırı yüklenemez ilgili işleçleri `&`, `*`, `->`, ve `[]`.</span><span class="sxs-lookup"><span data-stu-id="91542-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="91542-186">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="91542-186">C# language specification</span></span>

<span data-ttu-id="91542-187">Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="91542-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="91542-188">Sabit ve taşınabilir değişkenleri</span><span class="sxs-lookup"><span data-stu-id="91542-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="91542-189">Address-of işleci</span><span class="sxs-lookup"><span data-stu-id="91542-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="91542-190">İşaretçi yöneltmesi</span><span class="sxs-lookup"><span data-stu-id="91542-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="91542-191">İşaretçi üye erişimi</span><span class="sxs-lookup"><span data-stu-id="91542-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="91542-192">İşaretçi öğe erişimi</span><span class="sxs-lookup"><span data-stu-id="91542-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="91542-193">İşaretçi aritmetiği</span><span class="sxs-lookup"><span data-stu-id="91542-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="91542-194">İşaretçi artırma ve azaltma</span><span class="sxs-lookup"><span data-stu-id="91542-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="91542-195">İşaretçi karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="91542-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="91542-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91542-196">See also</span></span>

- [<span data-ttu-id="91542-197">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="91542-197">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="91542-198">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="91542-198">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="91542-199">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="91542-199">C# Operators</span></span>](index.md)
- [<span data-ttu-id="91542-200">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="91542-200">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="91542-201">`unsafe` Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="91542-201">`unsafe` keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="91542-202">`fixed` Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="91542-202">`fixed` keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="91542-203">`stackalloc` İşleci</span><span class="sxs-lookup"><span data-stu-id="91542-203">`stackalloc` operator</span></span>](stackalloc.md)
- [<span data-ttu-id="91542-204">`sizeof` İşleci</span><span class="sxs-lookup"><span data-stu-id="91542-204">`sizeof` operator</span></span>](../keywords/sizeof.md)
