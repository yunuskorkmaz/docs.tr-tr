---
title: '* Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 76ba0d9ac9ea6a2859dda31988588c3b3dd21807
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632913"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2553d-102">\* işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2553d-102">\* operator (C# Reference)</span></span>

<span data-ttu-id="2553d-103">`*` İşleci iki biçimde desteklenir: Birli işaretçi yöneltme işleci veya bir ikili çarpma işleci.</span><span class="sxs-lookup"><span data-stu-id="2553d-103">The `*` operator is supported in two forms: a unary pointer indirection operator or a binary multiplication operator.</span></span>

## <a name="pointer-indirection-operator"></a><span data-ttu-id="2553d-104">İşaretçi yöneltme işleci</span><span class="sxs-lookup"><span data-stu-id="2553d-104">Pointer indirection operator</span></span>

<span data-ttu-id="2553d-105">Birli kullanın `*` işleci bir işlenen bir işaretçi türünün işaret ettiği değişken elde edilir.</span><span class="sxs-lookup"><span data-stu-id="2553d-105">Use the unary `*` operator to obtain the variable to which an operand of a pointer type points.</span></span> <span data-ttu-id="2553d-106">Daha fazla bilgi için [nasıl yapılır: işaretçi değişkeninin değerini edinme](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md).</span><span class="sxs-lookup"><span data-stu-id="2553d-106">For more information, see [How to: obtain the value of a pointer variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md).</span></span>

<span data-ttu-id="2553d-107">İşaretçi yöneltme işleci `*` gerektirir [güvenli](../keywords/unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="2553d-107">The pointer indirection operator `*` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="multiplication-operator"></a><span data-ttu-id="2553d-108">Çarpma işleci</span><span class="sxs-lookup"><span data-stu-id="2553d-108">Multiplication operator</span></span>

<span data-ttu-id="2553d-109">Sayısal türlerin `*` işleci işlenenleri çarpımını hesaplar:</span><span class="sxs-lookup"><span data-stu-id="2553d-109">For numeric types, the `*` operator computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#Multiply)]

## <a name="operator-overloadability"></a><span data-ttu-id="2553d-110">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="2553d-110">Operator overloadability</span></span>

<span data-ttu-id="2553d-111">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) bir ikili `*` işleci.</span><span class="sxs-lookup"><span data-stu-id="2553d-111">User-defined types can [overload](../keywords/operator.md) a binary `*` operator.</span></span> <span data-ttu-id="2553d-112">Bir ikili olduğunda `*` işleci aşırı yüklenmiş, [çarpma atama işleci](multiplication-assignment-operator.md) `*=` aynı zamanda örtük olarak aşırı yüklenmiş olan.</span><span class="sxs-lookup"><span data-stu-id="2553d-112">When a binary `*` operator is overloaded, the [multiplication assignment operator](multiplication-assignment-operator.md) `*=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2553d-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="2553d-113">C# language specification</span></span>

<span data-ttu-id="2553d-114">Daha fazla bilgi için [işaretçi yöneltmesi](~/_csharplang/spec/unsafe-code.md#pointer-indirection) ve [çarpma işleci](~/_csharplang/spec/expressions.md#multiplication-operator) bölümlerini [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="2553d-114">For more information, see the [Pointer indirection](~/_csharplang/spec/unsafe-code.md#pointer-indirection) and [Multiplication operator](~/_csharplang/spec/expressions.md#multiplication-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2553d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2553d-115">See also</span></span>

- [<span data-ttu-id="2553d-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2553d-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2553d-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2553d-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2553d-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="2553d-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="2553d-119">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="2553d-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
