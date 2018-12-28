---
title: '&gt; Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
ms.openlocfilehash: 0c9d414d159b5e2f1faa24e9bd5f073d1ca874a4
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655978"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="3a4bc-102">&gt; İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3a4bc-102">&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="3a4bc-103">"Büyüktür" ilişkisel işleç `>` döndürür `true` , ikinci işlenenin ilk işlenenin büyükse `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="3a4bc-103">The "greater than" relational operator `>` returns `true` if its first operand is greater than its second operand, `false` otherwise.</span></span> <span data-ttu-id="3a4bc-104">Tüm sayısal ve Numaralandırma türleri desteği `>` işleci.</span><span class="sxs-lookup"><span data-stu-id="3a4bc-104">All numeric and enumeration types support the `>` operator.</span></span> <span data-ttu-id="3a4bc-105">Aynı işlenenleri için [enum](../keywords/enum.md) türü, temel alınan integral türünün karşılık gelen değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="3a4bc-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="3a4bc-106">İlişkisel işleçler için `==`, `>`, `<`, `>=`, ve `<=`herhangi bir işlenen değil, bir sayı (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>) işleminin sonucudur `false`.</span><span class="sxs-lookup"><span data-stu-id="3a4bc-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="3a4bc-107">Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) değeri.</span><span class="sxs-lookup"><span data-stu-id="3a4bc-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="3a4bc-108">Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.</span><span class="sxs-lookup"><span data-stu-id="3a4bc-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="3a4bc-109">Aşağıdaki örnek, kullanımını gösterir. `>` işleci:</span><span class="sxs-lookup"><span data-stu-id="3a4bc-109">The following example demonstrates the usage of the `>` operator:</span></span>

[!code-csharp-interactive[greater than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Greater)]

## <a name="operator-overloadability"></a><span data-ttu-id="3a4bc-110">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="3a4bc-110">Operator overloadability</span></span>

<span data-ttu-id="3a4bc-111">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `>` işleci.</span><span class="sxs-lookup"><span data-stu-id="3a4bc-111">User-defined types can [overload](../keywords/operator.md) the `>` operator.</span></span> <span data-ttu-id="3a4bc-112">Bir tür "büyüktür" işleci aşırı `>`, ayrıca aşırı gerekir ["az" işleci](less-than-operator.md) `<`.</span><span class="sxs-lookup"><span data-stu-id="3a4bc-112">If a type overloads the "greater than" operator `>`, it must also overload the ["less than" operator](less-than-operator.md) `<`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3a4bc-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3a4bc-113">C# language specification</span></span>

<span data-ttu-id="3a4bc-114">Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3a4bc-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3a4bc-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a4bc-115">See also</span></span>

- [<span data-ttu-id="3a4bc-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3a4bc-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3a4bc-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3a4bc-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3a4bc-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="3a4bc-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="3a4bc-119">>= İşleci</span><span class="sxs-lookup"><span data-stu-id="3a4bc-119">>= Operator</span></span>](greater-than-equal-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
