---
title: << işleci - C# başvurusu
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: deea2d0f720ba7f096e65c67378586bc88f24673
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219443"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="28cd8-102">\<\< İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="28cd8-102">\<\< operator (C# Reference)</span></span>

<span data-ttu-id="28cd8-103">Sola kaydırma işleci `<<` ilk işleneni sol tarafından ikinci işleneni tarafından tanımlanan bit sayısı kadar kaydırır.</span><span class="sxs-lookup"><span data-stu-id="28cd8-103">The left-shift operator `<<` shifts its first operand left by the number of bits defined by its second operand.</span></span> <span data-ttu-id="28cd8-104">Tüm tamsayı türlerini destekleyen `<<` işleci.</span><span class="sxs-lookup"><span data-stu-id="28cd8-104">All integer types support the `<<` operator.</span></span> <span data-ttu-id="28cd8-105">Ancak, ikinci işlenenin türünde olmalıdır [int](../keywords/int.md) veya olan bir türü bir [örtülü sayısal dönüştürme önceden tanımlanmış](../keywords/implicit-numeric-conversions-table.md) için `int`.</span><span class="sxs-lookup"><span data-stu-id="28cd8-105">However, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="28cd8-106">Sonuç türü aralığının dışında olan yüksek sıra bitleri atılır ve düşük düzey boş bit konumları, aşağıdaki örnekte gösterildiği gibi sıfır olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="28cd8-106">The high-order bits that are outside the range of the result type are discarded, and the low-order empty bit positions are set to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShift)]

## <a name="shift-count"></a><span data-ttu-id="28cd8-107">Kaydırma sayısı</span><span class="sxs-lookup"><span data-stu-id="28cd8-107">Shift count</span></span>

<span data-ttu-id="28cd8-108">İfade için `x << count`, gerçek kaydırma sayısı türüne bağlıdır `x` gibi:</span><span class="sxs-lookup"><span data-stu-id="28cd8-108">For the expression `x << count`, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="28cd8-109">Varsa türünü `x` olduğu [int](../keywords/int.md) veya [uint](../keywords/uint.md), kaydırma sayısı düşük düzey tarafından verilen *beş* ikinci işlenenin bit.</span><span class="sxs-lookup"><span data-stu-id="28cd8-109">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is given by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="28cd8-110">Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x1F` (veya `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="28cd8-110">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="28cd8-111">Varsa türünü `x` olduğu [uzun](../keywords/long.md) veya [ulong](../keywords/ulong.md), kaydırma sayısı düşük düzey tarafından verilen *altı* ikinci işlenenin bit.</span><span class="sxs-lookup"><span data-stu-id="28cd8-111">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is given by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="28cd8-112">Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x3F` (veya `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="28cd8-112">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="28cd8-113">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="28cd8-113">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftByLargeCount)]

## <a name="remarks"></a><span data-ttu-id="28cd8-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28cd8-114">Remarks</span></span>

<span data-ttu-id="28cd8-115">Kaydırma işleçlerini hiçbir zaman taşıyor neden ve aynı sonuçlar [checked ve unchecked](../keywords/checked-and-unchecked.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="28cd8-115">Shift operations never cause overflows and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="28cd8-116">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="28cd8-116">Operator overloadability</span></span>

<span data-ttu-id="28cd8-117">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `<<` işleci.</span><span class="sxs-lookup"><span data-stu-id="28cd8-117">User-defined types can [overload](../keywords/operator.md) the `<<` operator.</span></span> <span data-ttu-id="28cd8-118">Kullanıcı tanımlı bir tür ederse `T` aşırı `<<` işleci, birinci işlenenin türü olmalıdır `T` ve ikinci işlenenin türünde olmalıdır `int`.</span><span class="sxs-lookup"><span data-stu-id="28cd8-118">If a user-defined type `T` overloads the `<<` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span> <span data-ttu-id="28cd8-119">Zaman `<<` işleci aşırı yüklenmiş, [sola kaydırma atama işleci](left-shift-assignment-operator.md) `<<=` aynı zamanda örtük olarak aşırı yüklenmiş olan.</span><span class="sxs-lookup"><span data-stu-id="28cd8-119">When the `<<` operator is overloaded, the [left-shift assignment operator](left-shift-assignment-operator.md) `<<=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="28cd8-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="28cd8-120">C# language specification</span></span>

<span data-ttu-id="28cd8-121">Daha fazla bilgi için [kaydırma işleçleri](~/_csharplang/spec/expressions.md#shift-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="28cd8-121">For more information, see the [Shift operators](~/_csharplang/spec/expressions.md#shift-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="28cd8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28cd8-122">See also</span></span>

- [<span data-ttu-id="28cd8-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="28cd8-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="28cd8-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="28cd8-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="28cd8-125">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="28cd8-125">C# Operators</span></span>](index.md)
- [<span data-ttu-id="28cd8-126">>> işleci</span><span class="sxs-lookup"><span data-stu-id="28cd8-126">>> operator</span></span>](right-shift-operator.md)
