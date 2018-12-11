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
ms.openlocfilehash: a799c0e37d6607e8ff72ab984ff5e540a4e11063
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236381"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="6775d-102">&amp; İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6775d-102">&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="6775d-103">`&` İşleci iki biçimde desteklenir: Adres bir tekli işleç veya bir ikili mantıksal işleç.</span><span class="sxs-lookup"><span data-stu-id="6775d-103">The `&` operator is supported in two forms: a unary address-of operator or a binary logical operator.</span></span>

## <a name="unary-address-of-operator"></a><span data-ttu-id="6775d-104">Birli adres işleci</span><span class="sxs-lookup"><span data-stu-id="6775d-104">Unary address-of operator</span></span>

<span data-ttu-id="6775d-105">Birli `&` işleci, işlenenin adresini verir.</span><span class="sxs-lookup"><span data-stu-id="6775d-105">The unary `&` operator returns the address of its operand.</span></span> <span data-ttu-id="6775d-106">Daha fazla bilgi için [nasıl yapılır: değişkenin adresini edinme](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="6775d-106">For more information, see [How to: obtain the address of a variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span></span>

<span data-ttu-id="6775d-107">Address-of işlecini `&` gerektirir [güvenli](../keywords/unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="6775d-107">The address-of operator `&` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="integer-logical-bitwise-and-operator"></a><span data-ttu-id="6775d-108">Tamsayı mantıksal bit düzeyinde AND işleci</span><span class="sxs-lookup"><span data-stu-id="6775d-108">Integer logical bitwise AND operator</span></span>

<span data-ttu-id="6775d-109">Tamsayı türleri için `&` hesaplar işlenenleri, mantıksal bit düzeyinde AND işleci:</span><span class="sxs-lookup"><span data-stu-id="6775d-109">For integer types, the `&` operator computes the logical bitwise AND of its operands:</span></span>

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> <span data-ttu-id="6775d-110">İkili sabit dizeler önceki örnekte [sunulan C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) ve [içinde Gelişmiş C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="6775d-110">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

<span data-ttu-id="6775d-111">Tamsayı türlerinde işlemler genellikle sabit listesi türlerinde izin verildiğinden `&` işlecini de destekler [enum](../keywords/enum.md) işlenen.</span><span class="sxs-lookup"><span data-stu-id="6775d-111">Because operations on integer types are generally allowed on enumeration types, the `&` operator also supports [enum](../keywords/enum.md) operands.</span></span>

## <a name="boolean-logical-and-operator"></a><span data-ttu-id="6775d-112">Boolean mantıksal AND işleci</span><span class="sxs-lookup"><span data-stu-id="6775d-112">Boolean logical AND operator</span></span>

<span data-ttu-id="6775d-113">İçin [bool](../keywords/bool.md) işlenenini `&` işlenenleri, mantıksal AND işleci hesaplar.</span><span class="sxs-lookup"><span data-stu-id="6775d-113">For [bool](../keywords/bool.md) operands, the `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="6775d-114">Sonucu `x & y` olduğu `true` hem `x` ve `y` olan `true`.</span><span class="sxs-lookup"><span data-stu-id="6775d-114">The result of `x & y` is `true` if both `x` and `y` are `true`.</span></span> <span data-ttu-id="6775d-115">Aksi halde sonuç, `false`.</span><span class="sxs-lookup"><span data-stu-id="6775d-115">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="6775d-116">`&` İşleci, birinci işlenenin değerlendirilir olsa bile her iki işlenen de değerlendirir `false`, sonuç olmalıdır böylece `false` ikinci işlenenin değerinden bağımsız olarak.</span><span class="sxs-lookup"><span data-stu-id="6775d-116">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span> <span data-ttu-id="6775d-117">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="6775d-117">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

<span data-ttu-id="6775d-118">[Koşullu AND işleci](conditional-and-operator.md) `&&` ayrıca mantıksal hesaplar ve yalnızca ilk işlenen değerlendirilirse işlenenleri ancak ikinci işlenenin değerlendirilir `true`.</span><span class="sxs-lookup"><span data-stu-id="6775d-118">The [conditional AND operator](conditional-and-operator.md) `&&` also computes the logical AND of its operands, but evaluates the second operand only if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="6775d-119">Boş değer atanabilir bool işlenenleri, davranışı için `&` işleci SQL'in üç değerli mantığı ile tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="6775d-119">For nullable bool operands, the behavior of the `&` operator is consistent with SQL's three-valued logic.</span></span> <span data-ttu-id="6775d-120">Daha fazla bilgi için [bool? türü](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) bölümünü [boş değer atanabilir türleri kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="6775d-120">For more information, see the [The bool? type](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="6775d-121">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="6775d-121">Operator overloadability</span></span>

<span data-ttu-id="6775d-122">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) ikili `&` işleci.</span><span class="sxs-lookup"><span data-stu-id="6775d-122">User-defined types can [overload](../keywords/operator.md) the binary `&` operator.</span></span> <span data-ttu-id="6775d-123">Bir ikili olduğunda `&` işleci aşırı yüklenmiş, [AND atama işleci](and-assignment-operator.md) `&=` aynı zamanda örtük olarak aşırı yüklenmiş olan.</span><span class="sxs-lookup"><span data-stu-id="6775d-123">When a binary `&` operator is overloaded, the [AND assignment operator](and-assignment-operator.md) `&=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6775d-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6775d-124">C# language specification</span></span>

<span data-ttu-id="6775d-125">Daha fazla bilgi için [address-of işlecini](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) ve [mantıksal işleçler](~/_csharplang/spec/expressions.md#logical-operators) bölümlerini [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6775d-125">For more information, see [The address-of operator](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) and [Logical operators](~/_csharplang/spec/expressions.md#logical-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6775d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6775d-126">See also</span></span>

- [<span data-ttu-id="6775d-127">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6775d-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6775d-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6775d-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6775d-129">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="6775d-129">C# Operators</span></span>](index.md)
- [<span data-ttu-id="6775d-130">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="6775d-130">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="6775d-131">| işleci</span><span class="sxs-lookup"><span data-stu-id="6775d-131">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="6775d-132">^ işleci</span><span class="sxs-lookup"><span data-stu-id="6775d-132">^ operator</span></span>](xor-operator.md)
- [<span data-ttu-id="6775d-133">~ işleci</span><span class="sxs-lookup"><span data-stu-id="6775d-133">~ operator</span></span>](bitwise-complement-operator.md)
- [<span data-ttu-id="6775d-134">& & işleci</span><span class="sxs-lookup"><span data-stu-id="6775d-134">&& operator</span></span>](conditional-and-operator.md)
