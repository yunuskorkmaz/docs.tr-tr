---
title: -- İşleci (C# Başvurusu)
ms.date: 11/26/2018
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 0858321d6fe192a55bc548f169c558542238a981
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153347"
---
# <a name="---operator-c-reference"></a><span data-ttu-id="c8dbc-102">-- İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c8dbc-102">-- Operator (C# Reference)</span></span>

<span data-ttu-id="c8dbc-103">Birli azaltma işleci `--` azaltır işleneniyle 1.</span><span class="sxs-lookup"><span data-stu-id="c8dbc-103">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="c8dbc-104">İki biçimde desteklenir: sonek azaltma işlecinin `x--`ve önek azaltma işleci `--x`.</span><span class="sxs-lookup"><span data-stu-id="c8dbc-104">It's supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

## <a name="postfix-decrement-operator"></a><span data-ttu-id="c8dbc-105">Sonek azaltma işleci</span><span class="sxs-lookup"><span data-stu-id="c8dbc-105">Postfix decrement operator</span></span>

<span data-ttu-id="c8dbc-106">Sonucu `x--` değeri `x` *önce* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="c8dbc-106">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixDecrement)]

## <a name="prefix-decrement-operator"></a><span data-ttu-id="c8dbc-107">Önek azaltma işleci</span><span class="sxs-lookup"><span data-stu-id="c8dbc-107">Prefix decrement operator</span></span>

<span data-ttu-id="c8dbc-108">Sonucu `--x` değeri `x` *sonra* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="c8dbc-108">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixDecrement)]

## <a name="remarks"></a><span data-ttu-id="c8dbc-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8dbc-109">Remarks</span></span>

<span data-ttu-id="c8dbc-110">Azaltma işleci tüm önceden tanımlanan [tam sayı türleri](../keywords/integral-types-table.md) (dahil olmak üzere [char](../keywords/char.md) türü), [kayan nokta türleri](../keywords/floating-point-types-table.md)ve tüm [enum](../keywords/enum.md) yazın.</span><span class="sxs-lookup"><span data-stu-id="c8dbc-110">The decrement operator is predefined for all [integral types](../keywords/integral-types-table.md) (including the [char](../keywords/char.md) type), [floating-point types](../keywords/floating-point-types-table.md), and any [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="c8dbc-111">Azaltma işlecinin işleneni, bir değişken olmalıdır bir [özelliği](../../programming-guide/classes-and-structs/properties.md) erişim veya [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) erişim.</span><span class="sxs-lookup"><span data-stu-id="c8dbc-111">An operand of the decrement operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="c8dbc-112">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="c8dbc-112">Operator overloadability</span></span>

<span data-ttu-id="c8dbc-113">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `--` işleci.</span><span class="sxs-lookup"><span data-stu-id="c8dbc-113">User-defined types can [overload](../keywords/operator.md) the `--` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c8dbc-114">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c8dbc-114">C# language specification</span></span>

<span data-ttu-id="c8dbc-115">Daha fazla bilgi için [sonek arttırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) ve [önek arttırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) bölümlerini [ C# dilbelirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c8dbc-115">For more information, see the [Postfix increment and decrement operators](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) and [Prefix increment and decrement operators](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c8dbc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8dbc-116">See also</span></span>

- [<span data-ttu-id="c8dbc-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c8dbc-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c8dbc-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c8dbc-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c8dbc-119">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c8dbc-119">C# Operators</span></span>](index.md)
- [<span data-ttu-id="c8dbc-120">++ İşleci</span><span class="sxs-lookup"><span data-stu-id="c8dbc-120">++ Operator</span></span>](increment-operator.md)
- [<span data-ttu-id="c8dbc-121">Nasıl yapılır: işaretçileri artırma ve azaltma</span><span class="sxs-lookup"><span data-stu-id="c8dbc-121">How to: increment and decrement pointers</span></span>](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
