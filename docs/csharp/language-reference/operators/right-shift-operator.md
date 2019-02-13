---
title: '>> Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 809cd2cab29d3378892ea224cf846e9d0909b073
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219730"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0704f-102">>> işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0704f-102">>> operator (C# Reference)</span></span>

<span data-ttu-id="0704f-103">Sağa kaydırma işleci `>>` ilk işlenenin ikinci işleneni tarafından tanımlanan bit sayısına göre sağa kaydırır.</span><span class="sxs-lookup"><span data-stu-id="0704f-103">The right-shift operator `>>` shifts its first operand right by the number of bits defined by its second operand.</span></span> <span data-ttu-id="0704f-104">Tüm tamsayı türlerini destekleyen `>>` işleci.</span><span class="sxs-lookup"><span data-stu-id="0704f-104">All integer types support the `>>` operator.</span></span> <span data-ttu-id="0704f-105">Ancak, ikinci işlenenin türünde olmalıdır [int](../keywords/int.md) veya olan bir türü bir [örtülü sayısal dönüştürme önceden tanımlanmış](../keywords/implicit-numeric-conversions-table.md) için `int`.</span><span class="sxs-lookup"><span data-stu-id="0704f-105">However, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="0704f-106">Sağa kaydırma işlemi alt sıra bitleri atar.</span><span class="sxs-lookup"><span data-stu-id="0704f-106">The right-shift operation discards the low-order bits.</span></span> <span data-ttu-id="0704f-107">Yüksek düzeyli boş bit konumları birinci işlenenin türünde şu şekilde göre ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="0704f-107">The high-order empty bit positions are set based on the type of the first operand as follows:</span></span>

- <span data-ttu-id="0704f-108">Birinci işlenenin türü ise [int](../keywords/int.md) veya [uzun](../keywords/long.md), sağa kaydırma işleci gerçekleştiren bir **aritmetik** shift: ilk en önemli bite (imza biti) değeri işlenen, yüksek sıralı boş bit konumlarına yayılır.</span><span class="sxs-lookup"><span data-stu-id="0704f-108">If the first operand is of type [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift operator performs an **arithmetic** shift: the value of the most significant bit (the sign bit) of the first operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="0704f-109">Diğer bir deyişle, ilk işlenen negatif ise yüksek düzeyli boş bit konumları sıfır olarak ayarlanır ve negatif ise birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0704f-109">That is, the high-order empty bit positions are set to zero if the first operand is non-negative and set to one if it's negative.</span></span>

- <span data-ttu-id="0704f-110">Birinci işlenenin türü ise [uint](../keywords/uint.md) veya [ulong](../keywords/ulong.md), sağa kaydırma işleci gerçekleştiren bir **mantıksal** shift: yüksek düzeyli boş bit konumları her zaman sıfır olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0704f-110">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift operator performs a **logical** shift: the high-order empty bit positions are always set to zero.</span></span>

<span data-ttu-id="0704f-111">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="0704f-111">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[right shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShift)]

## <a name="shift-count"></a><span data-ttu-id="0704f-112">Kaydırma sayısı</span><span class="sxs-lookup"><span data-stu-id="0704f-112">Shift count</span></span>

<span data-ttu-id="0704f-113">İfade için `x >> count`, gerçek kaydırma sayısı türüne bağlıdır `x` gibi:</span><span class="sxs-lookup"><span data-stu-id="0704f-113">For the expression `x >> count`, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="0704f-114">Varsa türünü `x` olduğu [int](../keywords/int.md) veya [uint](../keywords/uint.md), kaydırma sayısı düşük düzey tarafından verilen *beş* ikinci işlenenin bit.</span><span class="sxs-lookup"><span data-stu-id="0704f-114">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is given by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="0704f-115">Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x1F` (veya `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="0704f-115">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="0704f-116">Varsa türünü `x` olduğu [uzun](../keywords/long.md) veya [ulong](../keywords/ulong.md), kaydırma sayısı düşük düzey tarafından verilen *altı* ikinci işlenenin bit.</span><span class="sxs-lookup"><span data-stu-id="0704f-116">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is given by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="0704f-117">Kaydırma sayısı gelen diğer bir deyişle, hesaplanan `count & 0x3F` (veya `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="0704f-117">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="0704f-118">Aşağıdaki örnek, bu davranış gösterir:</span><span class="sxs-lookup"><span data-stu-id="0704f-118">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftByLargeCount)]

## <a name="remarks"></a><span data-ttu-id="0704f-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0704f-119">Remarks</span></span>

<span data-ttu-id="0704f-120">Kaydırma işleçlerini hiçbir zaman taşıyor neden ve aynı sonuçlar [checked ve unchecked](../keywords/checked-and-unchecked.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="0704f-120">Shift operations never cause overflows and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="0704f-121">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="0704f-121">Operator overloadability</span></span>

<span data-ttu-id="0704f-122">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `>>` işleci.</span><span class="sxs-lookup"><span data-stu-id="0704f-122">User-defined types can [overload](../keywords/operator.md) the `>>` operator.</span></span> <span data-ttu-id="0704f-123">Kullanıcı tanımlı bir tür ederse `T` aşırı `>>` işleci, birinci işlenenin türü olmalıdır `T` ve ikinci işlenenin türünde olmalıdır `int`.</span><span class="sxs-lookup"><span data-stu-id="0704f-123">If a user-defined type `T` overloads the `>>` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span> <span data-ttu-id="0704f-124">Zaman `>>` işleci aşırı yüklenmiş, [sağa kaydırma atama işleci](right-shift-assignment-operator.md) `>>=` aynı zamanda örtük olarak aşırı yüklenmiş olan.</span><span class="sxs-lookup"><span data-stu-id="0704f-124">When the `>>` operator is overloaded, the [right-shift assignment operator](right-shift-assignment-operator.md) `>>=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0704f-125">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0704f-125">C# language specification</span></span>

<span data-ttu-id="0704f-126">Daha fazla bilgi için [kaydırma işleçleri](~/_csharplang/spec/expressions.md#shift-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0704f-126">For more information, see the [Shift operators](~/_csharplang/spec/expressions.md#shift-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0704f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0704f-127">See also</span></span>

- [<span data-ttu-id="0704f-128">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0704f-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0704f-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0704f-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0704f-130">C#işleçleri</span><span class="sxs-lookup"><span data-stu-id="0704f-130">C# operators</span></span>](index.md)
- [<span data-ttu-id="0704f-131"><< işleci</span><span class="sxs-lookup"><span data-stu-id="0704f-131"><< operator</span></span>](left-shift-operator.md)