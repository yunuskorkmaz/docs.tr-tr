---
title: ++ İşleci (C# Başvurusu)
ms.date: 11/26/2018
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: b29f4f1ab00c0f8026f118cb72b090e3b728bfc5
ms.sourcegitcommit: 6ae7cdd0437a32884556dd4826ca90e957b7a4e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2018
ms.locfileid: "48030476"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="75dcb-102">++ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="75dcb-102">++ Operator (C# Reference)</span></span>

<span data-ttu-id="75dcb-103">Tekli artırma işleci `++` işleneniyle 1 artar.</span><span class="sxs-lookup"><span data-stu-id="75dcb-103">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="75dcb-104">İki biçimde desteklenir: sonek artırma işlecini `x++`ve önek artırma işleci `++x`.</span><span class="sxs-lookup"><span data-stu-id="75dcb-104">It's supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

## <a name="postfix-increment-operator"></a><span data-ttu-id="75dcb-105">Sonek artırma işleci</span><span class="sxs-lookup"><span data-stu-id="75dcb-105">Postfix increment operator</span></span>

<span data-ttu-id="75dcb-106">Sonucu `x++` değeri `x` *önce* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="75dcb-106">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixIncrement)]

## <a name="prefix-increment-operator"></a><span data-ttu-id="75dcb-107">Önek artırma işleci</span><span class="sxs-lookup"><span data-stu-id="75dcb-107">Prefix increment operator</span></span>

<span data-ttu-id="75dcb-108">Sonucu `++x` değeri `x` *sonra* aşağıdaki örnekte gösterildiği gibi işlem:</span><span class="sxs-lookup"><span data-stu-id="75dcb-108">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixIncrement)]

## <a name="remarks"></a><span data-ttu-id="75dcb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75dcb-109">Remarks</span></span>

<span data-ttu-id="75dcb-110">Artırım işleci tüm önceden tanımlanan [tam sayı türleri](../keywords/integral-types-table.md) (dahil olmak üzere [char](../keywords/char.md) türü), [kayan nokta türleri](../keywords/floating-point-types-table.md)ve tüm [enum](../keywords/enum.md) yazın.</span><span class="sxs-lookup"><span data-stu-id="75dcb-110">The increment operator is predefined for all [integral types](../keywords/integral-types-table.md) (including the [char](../keywords/char.md) type), [floating-point types](../keywords/floating-point-types-table.md), and any [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="75dcb-111">Artırma işlecinin işleneni, bir değişken olmalıdır bir [özelliği](../../programming-guide/classes-and-structs/properties.md) erişim veya [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) erişim.</span><span class="sxs-lookup"><span data-stu-id="75dcb-111">An operand of the increment operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="75dcb-112">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="75dcb-112">Operator overloadability</span></span>

<span data-ttu-id="75dcb-113">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `++` işleci.</span><span class="sxs-lookup"><span data-stu-id="75dcb-113">User-defined types can [overload](../keywords/operator.md) the `++` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="75dcb-114">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="75dcb-114">C# language specification</span></span>

<span data-ttu-id="75dcb-115">Daha fazla bilgi için [sonek arttırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) ve [önek arttırma ve azaltma işleçleri](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) bölümlerini [ C# dilbelirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="75dcb-115">For more information, see the [Postfix increment and decrement operators](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) and [Prefix increment and decrement operators](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75dcb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75dcb-116">See also</span></span>

- [<span data-ttu-id="75dcb-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="75dcb-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="75dcb-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="75dcb-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="75dcb-119">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="75dcb-119">C# Operators</span></span>](index.md)
- [<span data-ttu-id="75dcb-120">-- İşleci</span><span class="sxs-lookup"><span data-stu-id="75dcb-120">-- Operator</span></span>](decrement-operator.md)
- [<span data-ttu-id="75dcb-121">Nasıl yapılır: işaretçileri artırma ve azaltma</span><span class="sxs-lookup"><span data-stu-id="75dcb-121">How to: increment and decrement pointers</span></span>](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
