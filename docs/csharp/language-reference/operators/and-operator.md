---
title: '&amp; Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 67d60709e1c6c76071ecfb7aac74c83dec6f372a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310050"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="db731-102">&amp; İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="db731-102">&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="db731-103">`&` İşleci iki biçimde desteklenir: Adres bir tekli işleç veya bir ikili mantıksal işleç.</span><span class="sxs-lookup"><span data-stu-id="db731-103">The `&` operator is supported in two forms: a unary address-of operator or a binary logical operator.</span></span>

## <a name="unary-address-of-operator"></a><span data-ttu-id="db731-104">Birli adres işleci</span><span class="sxs-lookup"><span data-stu-id="db731-104">Unary address-of operator</span></span>

<span data-ttu-id="db731-105">Birli `&` işleci, işlenenin adresini verir.</span><span class="sxs-lookup"><span data-stu-id="db731-105">The unary `&` operator returns the address of its operand.</span></span> <span data-ttu-id="db731-106">Daha fazla bilgi için [nasıl yapılır: değişkenin adresini edinme](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="db731-106">For more information, see [How to: obtain the address of a variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span></span>

<span data-ttu-id="db731-107">Address-of işlecini `&` gerektirir [güvenli](../keywords/unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="db731-107">The address-of operator `&` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="integer-logical-bitwise-and-operator"></a><span data-ttu-id="db731-108">Tamsayı mantıksal bit düzeyinde AND işleci</span><span class="sxs-lookup"><span data-stu-id="db731-108">Integer logical bitwise AND operator</span></span>

<span data-ttu-id="db731-109">Tamsayı türleri için `&` hesaplar işlenenleri, mantıksal bit düzeyinde AND işleci:</span><span class="sxs-lookup"><span data-stu-id="db731-109">For integer types, the `&` operator computes the logical bitwise AND of its operands:</span></span>

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> <span data-ttu-id="db731-110">İkili sabit dizeler önceki örnekte [sunulan C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) ve [içinde Gelişmiş C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="db731-110">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

<span data-ttu-id="db731-111">Tamsayı türlerinde işlemler genellikle sabit listesi türlerinde izin verildiğinden `&` işlecini de destekler [enum](../keywords/enum.md) işlenen.</span><span class="sxs-lookup"><span data-stu-id="db731-111">Because operations on integer types are generally allowed on enumeration types, the `&` operator also supports [enum](../keywords/enum.md) operands.</span></span>

## <a name="boolean-logical-and-operator"></a><span data-ttu-id="db731-112">Boolean mantıksal AND işleci</span><span class="sxs-lookup"><span data-stu-id="db731-112">Boolean logical AND operator</span></span>

<span data-ttu-id="db731-113">İçin [bool](../keywords/bool.md) işlenenini `&` işlenenleri, mantıksal AND işleci hesaplar.</span><span class="sxs-lookup"><span data-stu-id="db731-113">For [bool](../keywords/bool.md) operands, the `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="db731-114">Sonucu `x & y` olduğu `true` hem `x` ve `y` olan `true`.</span><span class="sxs-lookup"><span data-stu-id="db731-114">The result of `x & y` is `true` if both `x` and `y` are `true`.</span></span> <span data-ttu-id="db731-115">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="db731-115">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="db731-116">`&` İşleci, birinci işlenenin değerlendirilir olsa bile her iki işlenen de değerlendirir `false`, sonuç olmalıdır böylece `false` ikinci işlenenin değerinden bağımsız olarak.</span><span class="sxs-lookup"><span data-stu-id="db731-116">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span> <span data-ttu-id="db731-117">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="db731-117">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

<span data-ttu-id="db731-118">[Koşullu AND işleci](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` ayrıca mantıksal ve işlenenleri, hesaplar, ancak değerlendirme sonucu ilk işlenen ikinci işlenende değerlendirmez `false`.</span><span class="sxs-lookup"><span data-stu-id="db731-118">The [conditional AND operator](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="db731-119">Boş değer atanabilir bool işlenenleri, davranışı için `&` işleci SQL'in üç değerli mantığı ile tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="db731-119">For nullable bool operands, the behavior of the `&` operator is consistent with SQL's three-valued logic.</span></span> <span data-ttu-id="db731-120">Daha fazla bilgi için [boş değer atanabilir Boolean mantıksal işleçler](boolean-logical-operators.md#nullable-boolean-logical-operators) bölümünü [Boolean mantıksal işleçler](boolean-logical-operators.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="db731-120">For more information, see the [Nullable Boolean logical operators](boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](boolean-logical-operators.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="db731-121">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="db731-121">Operator overloadability</span></span>

<span data-ttu-id="db731-122">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) ikili `&` işleci.</span><span class="sxs-lookup"><span data-stu-id="db731-122">User-defined types can [overload](../keywords/operator.md) the binary `&` operator.</span></span> <span data-ttu-id="db731-123">Bir ikili olduğunda `&` işleci aşırı yüklenmiş, [AND atama işleci](and-assignment-operator.md) `&=` aynı zamanda örtük olarak aşırı yüklenmiş olan.</span><span class="sxs-lookup"><span data-stu-id="db731-123">When a binary `&` operator is overloaded, the [AND assignment operator](and-assignment-operator.md) `&=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="db731-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="db731-124">C# language specification</span></span>

<span data-ttu-id="db731-125">Daha fazla bilgi için [address-of işlecini](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) ve [mantıksal işleçler](~/_csharplang/spec/expressions.md#logical-operators) bölümlerini [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="db731-125">For more information, see [The address-of operator](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) and [Logical operators](~/_csharplang/spec/expressions.md#logical-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db731-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db731-126">See also</span></span>

- [<span data-ttu-id="db731-127">C# Başvurusu</span><span class="sxs-lookup"><span data-stu-id="db731-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="db731-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="db731-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="db731-129">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="db731-129">C# Operators</span></span>](index.md)
- [<span data-ttu-id="db731-130">Boole mantıksal işleçleri</span><span class="sxs-lookup"><span data-stu-id="db731-130">Boolean logical operators</span></span>](boolean-logical-operators.md)
- [<span data-ttu-id="db731-131">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="db731-131">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="db731-132">| işleci</span><span class="sxs-lookup"><span data-stu-id="db731-132">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="db731-133">^ işleci</span><span class="sxs-lookup"><span data-stu-id="db731-133">^ operator</span></span>](xor-operator.md)
- [<span data-ttu-id="db731-134">~ işleci</span><span class="sxs-lookup"><span data-stu-id="db731-134">~ operator</span></span>](bitwise-complement-operator.md)
