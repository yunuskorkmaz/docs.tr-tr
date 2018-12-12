---
title: / İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 45bcd64b60e7d13f389064faefeda815ea1f32c9
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286539"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7d509-102">/ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7d509-102">/ Operator (C# Reference)</span></span>

<span data-ttu-id="7d509-103">Bölme işleci `/` ilk işlenenin ikinci işleneni olarak böler.</span><span class="sxs-lookup"><span data-stu-id="7d509-103">The division operator `/` divides its first operand by its second operand.</span></span> <span data-ttu-id="7d509-104">Tüm sayısal türler, bölme işleci destekler.</span><span class="sxs-lookup"><span data-stu-id="7d509-104">All numeric types support the division operator.</span></span>

## <a name="integer-division"></a><span data-ttu-id="7d509-105">Tamsayı bölme</span><span class="sxs-lookup"><span data-stu-id="7d509-105">Integer division</span></span>

<span data-ttu-id="7d509-106">Tamsayı türleri sonucunu işlenenleri için `/` işleci bir tamsayı türüdür ve sayının yuvarlanmış sıfır iki işlenenden eşittir:</span><span class="sxs-lookup"><span data-stu-id="7d509-106">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#Integer)]

<span data-ttu-id="7d509-107">İki işlenenden bölümü bir kayan noktalı sayı olarak almak için kullanın `float`, `double`, veya `decimal` türü:</span><span class="sxs-lookup"><span data-stu-id="7d509-107">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#IntegerAsFloatingPoint)]

## <a name="floating-point-division"></a><span data-ttu-id="7d509-108">Kayan nokta bölme</span><span class="sxs-lookup"><span data-stu-id="7d509-108">Floating-point division</span></span>

<span data-ttu-id="7d509-109">İçin `float`, `double`, ve `decimal` türleri, sonucunu `/` işleci, iki işlenenden bölümü:</span><span class="sxs-lookup"><span data-stu-id="7d509-109">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#FloatingPoint)]

<span data-ttu-id="7d509-110">İşlenenler ise `decimal`, başka bir işleç ne olabilir `float` ya da `double`, çünkü ne `float` ya da `double` örtük olarak dönüştürülebilir `decimal`.</span><span class="sxs-lookup"><span data-stu-id="7d509-110">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="7d509-111">Açıkça dönüştürmelisiniz `float` veya `double` işleneni `decimal` türü.</span><span class="sxs-lookup"><span data-stu-id="7d509-111">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="7d509-112">Sayısal türler arasında örtük dönüştürme hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="7d509-112">For more information about implicit conversions between numeric types, see [Implicit numeric conversions table](../keywords/implicit-numeric-conversions-table.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="7d509-113">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="7d509-113">Operator overloadability</span></span>

<span data-ttu-id="7d509-114">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `/` işleci.</span><span class="sxs-lookup"><span data-stu-id="7d509-114">User-defined types can [overload](../keywords/operator.md) the `/` operator.</span></span> <span data-ttu-id="7d509-115">Zaman `/` işleci aşırı yüklenmiş, [bölme atama işleci](division-assignment-operator.md) `/=` aynı zamanda örtük olarak aşırı yüklenmiş olan.</span><span class="sxs-lookup"><span data-stu-id="7d509-115">When the `/` operator is overloaded, the [division assignment operator](division-assignment-operator.md) `/=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7d509-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7d509-116">C# language specification</span></span>

<span data-ttu-id="7d509-117">Daha fazla bilgi için [bölme işleci](~/_csharplang/spec/expressions.md#division-operator) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="7d509-117">For more information, see the [Division operator](~/_csharplang/spec/expressions.md#division-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d509-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d509-118">See also</span></span>

- [<span data-ttu-id="7d509-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7d509-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7d509-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7d509-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7d509-121">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="7d509-121">C# Operators</span></span>](index.md)
- [<span data-ttu-id="7d509-122">% İşleci</span><span class="sxs-lookup"><span data-stu-id="7d509-122">% Operator</span></span>](remainder-operator.md)
