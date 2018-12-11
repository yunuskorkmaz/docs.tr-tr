---
title: '% İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 09/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: a5c12b6683e35cc1ec2d40446dd0ed068c3d2552
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236485"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4848f-102">% İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4848f-102">% Operator (C# Reference)</span></span>

<span data-ttu-id="4848f-103">Kalan işleci `%` ilk işlenenin ikinci işleneni tarafından bölme işleminden kalanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="4848f-103">The remainder operator `%` computes the remainder after dividing its first operand by its second operand.</span></span>

<span data-ttu-id="4848f-104">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `%` işleci.</span><span class="sxs-lookup"><span data-stu-id="4848f-104">User-defined types can [overload](../keywords/operator.md) the `%` operator.</span></span> <span data-ttu-id="4848f-105">Zaman `%` aşırı yüklendi [kalan atama işleci](remainder-assignment-operator.md) `%=` aynı zamanda örtük olarak aşırı yüklenmiş olan.</span><span class="sxs-lookup"><span data-stu-id="4848f-105">When the `%` is overloaded, the [remainder assignment operator](remainder-assignment-operator.md) `%=` is also implicitly overloaded.</span></span>

<span data-ttu-id="4848f-106">Kalan işleci tüm sayısal türlerin destekler.</span><span class="sxs-lookup"><span data-stu-id="4848f-106">All numeric types support the remainder operator.</span></span>

## <a name="integer-remainder"></a><span data-ttu-id="4848f-107">Tamsayı kalan</span><span class="sxs-lookup"><span data-stu-id="4848f-107">Integer remainder</span></span>
  
<span data-ttu-id="4848f-108">Sonucu tamsayı işlenenleri için `a % b` değeri tarafından üretilen `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="4848f-108">For the integer operands, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="4848f-109">Sıfır olmayan kalanı oturum, ilk işlenen, aşağıdaki örnekte gösterildiği gibi aynıdır:</span><span class="sxs-lookup"><span data-stu-id="4848f-109">The sign of the non-zero remainder is the same as that of the first operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#1)]

## <a name="floating-point-remainder"></a><span data-ttu-id="4848f-110">Kayan nokta kalanını</span><span class="sxs-lookup"><span data-stu-id="4848f-110">Floating-point remainder</span></span>

<span data-ttu-id="4848f-111">İçin [float](../keywords/float.md) ve [çift](../keywords/double.md) işlenenler, sonucunu `x % y` sınırlı için `x` ve `y` değer `z` gibi</span><span class="sxs-lookup"><span data-stu-id="4848f-111">For the [float](../keywords/float.md) and [double](../keywords/double.md) operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="4848f-112">işaretini `z`, sıfır olmayan, işaretini aynı `x`;</span><span class="sxs-lookup"><span data-stu-id="4848f-112">the sign of `z`, if non-zero, is the same as the sign of `x`;</span></span>
- <span data-ttu-id="4848f-113">mutlak değerini `z` değeri tarafından üretilen `|x| - n * |y|` burada `n` küçük veya eşit en büyük olası tamsayı `|x| / |y|` ve `|x|` ve `|y|` mutlak değerleri `x` ve `y`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="4848f-113">the absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

<span data-ttu-id="4848f-114">Davranışı hakkında bilgi için `%` sonlu olmayan işlenenler işleç bkz [kalan işleci](~/_csharplang/spec/expressions.md#remainder-operator) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4848f-114">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4848f-115">Kalanı hesaplama, bu yöntem, tamsayı işlenenler için kullanılan benzer, ancak IEEE 754 farklıdır.</span><span class="sxs-lookup"><span data-stu-id="4848f-115">This method of computing the remainder is analogous to that used for integer operands, but differs from the IEEE 754.</span></span> <span data-ttu-id="4848f-116">IEEE 754 ile uyumlu işlemini ihtiyacınız varsa, <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4848f-116">If you need the remainder operation that complies with the IEEE 754, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="4848f-117">Aşağıdaki örnek için kalan işleci davranışını gösterir `float` ve `double` işlenenler:</span><span class="sxs-lookup"><span data-stu-id="4848f-117">The following example demonstrates the behavior of the remainder operator for `float` and `double` operands:</span></span>

[!code-csharp-interactive[float and double remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#2)]

<span data-ttu-id="4848f-118">Kayan nokta türleri ile ilişkilendirilebilen yuvarlama hataları unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4848f-118">Note the round-off errors that can be associated with the floating-point types.</span></span>

<span data-ttu-id="4848f-119">İçin [ondalık](../keywords/decimal.md) işlenenler, kalan işleci `%` eşdeğerdir [kalan işleci](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) , <xref:System.Decimal?displayProperty=nameWithType> türü.</span><span class="sxs-lookup"><span data-stu-id="4848f-119">For the [decimal](../keywords/decimal.md) operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

## <a name="see-also"></a><span data-ttu-id="4848f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4848f-120">See also</span></span>

- [<span data-ttu-id="4848f-121">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4848f-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4848f-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4848f-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4848f-123">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="4848f-123">C# Operators</span></span>](index.md)
- <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>
- <xref:System.Math.DivRem%2A?displayProperty=nameWithType>
