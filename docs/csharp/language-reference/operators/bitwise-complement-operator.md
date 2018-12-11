---
title: ~ İşleci (C# Başvurusu)
ms.date: 11/05/2018
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 1bcb07c5639a098e3a8c566e92083ca0d48efb81
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153221"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0b42e-102">~ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0b42e-102">~ Operator (C# Reference)</span></span>

<span data-ttu-id="0b42e-103">Bit düzeyinde tamamlama işleci `~` bir bit düzeyinde tamamlayıcı işlenenin her bitini ters çevirerek üreten bir birli işleç.</span><span class="sxs-lookup"><span data-stu-id="0b42e-103">The bitwise complement operator `~` is a unary operator that produces a bitwise complement of its operand by reversing each bit.</span></span> <span data-ttu-id="0b42e-104">Tüm tamsayı türlerini destekleyen `~` işleci.</span><span class="sxs-lookup"><span data-stu-id="0b42e-104">All integer types support the `~` operator.</span></span>

> [!NOTE]
> <span data-ttu-id="0b42e-105">`~` Simgesi sonlandırıcılar bildirmek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b42e-105">The `~` symbol is also used to declare finalizers.</span></span> <span data-ttu-id="0b42e-106">Daha fazla bilgi için [sonlandırıcılar](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="0b42e-106">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

<span data-ttu-id="0b42e-107">Aşağıdaki örnek, kullanımını gösterir. `~` işleci:</span><span class="sxs-lookup"><span data-stu-id="0b42e-107">The following example demonstrates the usage of the `~` operator:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseComplementExamples.cs#Example)]

> [!NOTE]
> <span data-ttu-id="0b42e-108">İkili sabit dizeler önceki örnekte [sunulan C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) ve [içinde Gelişmiş C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="0b42e-108">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced  in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="0b42e-109">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="0b42e-109">Operator overloadability</span></span>

<span data-ttu-id="0b42e-110">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `~` işleci.</span><span class="sxs-lookup"><span data-stu-id="0b42e-110">User-defined types can [overload](../keywords/operator.md) the `~` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0b42e-111">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0b42e-111">C# language specification</span></span>

<span data-ttu-id="0b42e-112">Daha fazla bilgi için [bit düzeyinde tamamlama işleci](~/_csharplang/spec/expressions.md#bitwise-complement-operator) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0b42e-112">For more information, see the [Bitwise complement operator](~/_csharplang/spec/expressions.md#bitwise-complement-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0b42e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b42e-113">See also</span></span>

- [<span data-ttu-id="0b42e-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0b42e-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0b42e-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0b42e-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0b42e-116">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="0b42e-116">C# Operators</span></span>](index.md)
- [<span data-ttu-id="0b42e-117">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="0b42e-117">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)
- [<span data-ttu-id="0b42e-118">& işleci</span><span class="sxs-lookup"><span data-stu-id="0b42e-118">& operator</span></span>](and-operator.md)
- [<span data-ttu-id="0b42e-119">| işleci</span><span class="sxs-lookup"><span data-stu-id="0b42e-119">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="0b42e-120">^ işleci</span><span class="sxs-lookup"><span data-stu-id="0b42e-120">^ operator</span></span>](xor-operator.md)
