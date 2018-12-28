---
title: '&lt;= İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
ms.openlocfilehash: 30f42de68667756a8233fef4241bfd74ed4eff2a
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656095"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="1c93c-102">&lt;= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1c93c-102">&lt;= Operator (C# Reference)</span></span>

<span data-ttu-id="1c93c-103">"Küçük veya eşit" ilişkisel işleç `<=` döndürür `true` ilk işlenenin ikinci işleneni, küçük veya ona eşit olup olmadığını `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="1c93c-103">The "less than or equal" relational operator `<=` returns `true` if its first operand is less than or equal to its second operand, `false` otherwise.</span></span> <span data-ttu-id="1c93c-104">Tüm sayısal ve Numaralandırma türleri desteği `<=` işleci.</span><span class="sxs-lookup"><span data-stu-id="1c93c-104">All numeric and enumeration types support the `<=` operator.</span></span> <span data-ttu-id="1c93c-105">Aynı işlenenleri için [enum](../keywords/enum.md) türü, temel alınan integral türünün karşılık gelen değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="1c93c-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="1c93c-106">İlişkisel işleçler için `==`, `>`, `<`, `>=`, ve `<=`herhangi bir işlenen değil, bir sayı (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>) işleminin sonucudur `false`.</span><span class="sxs-lookup"><span data-stu-id="1c93c-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="1c93c-107">Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) değeri.</span><span class="sxs-lookup"><span data-stu-id="1c93c-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="1c93c-108">Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.</span><span class="sxs-lookup"><span data-stu-id="1c93c-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="1c93c-109">Aşağıdaki örnek, kullanımını gösterir. `<=` işleci:</span><span class="sxs-lookup"><span data-stu-id="1c93c-109">The following example demonstrates the usage of the `<=` operator:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#LessOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="1c93c-110">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="1c93c-110">Operator overloadability</span></span>

<span data-ttu-id="1c93c-111">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `<=` işleci.</span><span class="sxs-lookup"><span data-stu-id="1c93c-111">User-defined types can [overload](../keywords/operator.md) the `<=` operator.</span></span> <span data-ttu-id="1c93c-112">Bir tür "küçüktür veya eşittir" işleci aşırı `<=`, ayrıca aşırı gerekir ["büyüktür veya eşittir" işleci](greater-than-equal-operator.md) `>=`.</span><span class="sxs-lookup"><span data-stu-id="1c93c-112">If a type overloads the "less than or equal" operator `<=`, it must also overload the ["greater than or equal" operator](greater-than-equal-operator.md) `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1c93c-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1c93c-113">C# language specification</span></span>

<span data-ttu-id="1c93c-114">Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="1c93c-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c93c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c93c-115">See also</span></span>

- [<span data-ttu-id="1c93c-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1c93c-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1c93c-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1c93c-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1c93c-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="1c93c-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="1c93c-119">< İşleci</span><span class="sxs-lookup"><span data-stu-id="1c93c-119">< Operator</span></span>](less-than-operator.md)
- [<span data-ttu-id="1c93c-120">== İşleci</span><span class="sxs-lookup"><span data-stu-id="1c93c-120">== Operator</span></span>](equality-comparison-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
