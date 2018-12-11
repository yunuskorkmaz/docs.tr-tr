---
title: ~ İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 11/05/2018
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 57e5baee423c0b5d9292d0ad4cbf909646eb3a38
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235731"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ac74a-102">~ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ac74a-102">~ Operator (C# Reference)</span></span>

<span data-ttu-id="ac74a-103">Bit düzeyinde tamamlama işleci `~` bir bit düzeyinde tamamlayıcı işlenenin her bitini ters çevirerek üreten bir birli işleç.</span><span class="sxs-lookup"><span data-stu-id="ac74a-103">The bitwise complement operator `~` is a unary operator that produces a bitwise complement of its operand by reversing each bit.</span></span> <span data-ttu-id="ac74a-104">Tüm tamsayı türlerini destekleyen `~` işleci.</span><span class="sxs-lookup"><span data-stu-id="ac74a-104">All integer types support the `~` operator.</span></span>

> [!NOTE]
> <span data-ttu-id="ac74a-105">`~` Simgesi sonlandırıcılar bildirmek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac74a-105">The `~` symbol is also used to declare finalizers.</span></span> <span data-ttu-id="ac74a-106">Daha fazla bilgi için [sonlandırıcılar](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="ac74a-106">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

<span data-ttu-id="ac74a-107">Aşağıdaki örnek, kullanımını gösterir. `~` işleci:</span><span class="sxs-lookup"><span data-stu-id="ac74a-107">The following example demonstrates the usage of the `~` operator:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseComplementExamples.cs#Example)]

> [!NOTE]
> <span data-ttu-id="ac74a-108">İkili sabit dizeler önceki örnekte [sunulan C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) ve [içinde Gelişmiş C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="ac74a-108">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced  in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ac74a-109">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="ac74a-109">Operator overloadability</span></span>

<span data-ttu-id="ac74a-110">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `~` işleci.</span><span class="sxs-lookup"><span data-stu-id="ac74a-110">User-defined types can [overload](../keywords/operator.md) the `~` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ac74a-111">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ac74a-111">C# language specification</span></span>

<span data-ttu-id="ac74a-112">Daha fazla bilgi için [bit düzeyinde tamamlama işleci](~/_csharplang/spec/expressions.md#bitwise-complement-operator) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ac74a-112">For more information, see the [Bitwise complement operator](~/_csharplang/spec/expressions.md#bitwise-complement-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac74a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac74a-113">See also</span></span>

- [<span data-ttu-id="ac74a-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ac74a-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ac74a-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ac74a-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ac74a-116">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="ac74a-116">C# Operators</span></span>](index.md)
- [<span data-ttu-id="ac74a-117">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="ac74a-117">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)
- [<span data-ttu-id="ac74a-118">& işleci</span><span class="sxs-lookup"><span data-stu-id="ac74a-118">& operator</span></span>](and-operator.md)
- [<span data-ttu-id="ac74a-119">| işleci</span><span class="sxs-lookup"><span data-stu-id="ac74a-119">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="ac74a-120">^ işleci</span><span class="sxs-lookup"><span data-stu-id="ac74a-120">^ operator</span></span>](xor-operator.md)
