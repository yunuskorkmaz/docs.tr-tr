---
title: '&gt;= İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- '>=_CSharpKeyword'
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
ms.openlocfilehash: 34437742d33cff97e53c6dfb163df083e80d41f3
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655939"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="d653b-102">&gt;= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d653b-102">&gt;= Operator (C# Reference)</span></span>

<span data-ttu-id="d653b-103">"Büyüktür veya eşittir" ilişkisel işleç `>=` döndürür `true` ilk işlenenin değerinden büyük veya eşittir, ikinci işleneni ise `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="d653b-103">The "greater than or equal" relational operator `>=` returns `true` if its first operand is greater than or equal to its second operand, `false` otherwise.</span></span> <span data-ttu-id="d653b-104">Tüm sayısal ve Numaralandırma türleri desteği `>=` işleci.</span><span class="sxs-lookup"><span data-stu-id="d653b-104">All numeric and  enumeration types support the `>=` operator.</span></span> <span data-ttu-id="d653b-105">Aynı işlenenleri için [enum](../keywords/enum.md) türü, temel alınan integral türünün karşılık gelen değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="d653b-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="d653b-106">İlişkisel işleçler için `==`, `>`, `<`, `>=`, ve `<=`herhangi bir işlenen değil, bir sayı (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>) işleminin sonucudur `false`.</span><span class="sxs-lookup"><span data-stu-id="d653b-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="d653b-107">Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) değeri.</span><span class="sxs-lookup"><span data-stu-id="d653b-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="d653b-108">Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.</span><span class="sxs-lookup"><span data-stu-id="d653b-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="d653b-109">Aşağıdaki örnek, kullanımını gösterir. `>=` işleci:</span><span class="sxs-lookup"><span data-stu-id="d653b-109">The following example demonstrates the usage of the `>=` operator:</span></span>

[!code-csharp-interactive[greater than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="d653b-110">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="d653b-110">Operator overloadability</span></span>

<span data-ttu-id="d653b-111">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `>=` işleci.</span><span class="sxs-lookup"><span data-stu-id="d653b-111">User-defined types can [overload](../keywords/operator.md) the `>=` operator.</span></span> <span data-ttu-id="d653b-112">Bir tür "büyüktür veya eşittir" işleci aşırı `>=`, ayrıca aşırı gerekir ["küçüktür veya eşittir" işleci](less-than-equal-operator.md) `<=`.</span><span class="sxs-lookup"><span data-stu-id="d653b-112">If a type overloads the "greater than or equal" operator `>=`, it must also overload the ["less than or equal" operator](less-than-equal-operator.md) `<=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d653b-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d653b-113">C# language specification</span></span>

<span data-ttu-id="d653b-114">Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d653b-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d653b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d653b-115">See also</span></span>

- [<span data-ttu-id="d653b-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d653b-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d653b-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d653b-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d653b-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d653b-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="d653b-119">> İşleci</span><span class="sxs-lookup"><span data-stu-id="d653b-119">> Operator</span></span>](greater-than-operator.md)
- [<span data-ttu-id="d653b-120">== İşleci</span><span class="sxs-lookup"><span data-stu-id="d653b-120">== Operator</span></span>](equality-comparison-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
