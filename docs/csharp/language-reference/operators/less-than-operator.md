---
title: < İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
ms.openlocfilehash: ab21e32b7609bc0c8753b42ccf8b6091bf3ad57b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286643"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6b7d5-102">\< İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6b7d5-102">\< Operator (C# Reference)</span></span>

<span data-ttu-id="6b7d5-103">"Az" ilişkisel işleç `<` döndürür `true` ilk işleneni küçükse değerinden ikinci işleneniyle `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="6b7d5-103">The "less than" relational operator `<` returns `true` if its first operand is less than its second operand, `false` otherwise.</span></span> <span data-ttu-id="6b7d5-104">Tüm sayısal ve Numaralandırma türleri desteği `<` işleci.</span><span class="sxs-lookup"><span data-stu-id="6b7d5-104">All numeric and enumeration types support the `<` operator.</span></span> <span data-ttu-id="6b7d5-105">Aynı işlenenleri için [enum](../keywords/enum.md) türü, temel alınan integral türünün karşılık gelen değerleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="6b7d5-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="6b7d5-106">İlişkisel işleçler için `==`, `>`, `<`, `>=`, ve `<=`herhangi bir işlenen değil, bir sayı (<xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType>) işleminin sonucudur `false`.</span><span class="sxs-lookup"><span data-stu-id="6b7d5-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="6b7d5-107">Bu anlamına `NaN` değerdir ne büyük, küçük ya da diğer eşit `double` (veya `float`) değeri.</span><span class="sxs-lookup"><span data-stu-id="6b7d5-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="6b7d5-108">Daha fazla bilgi ve örnekler için bkz. <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> başvurusu makalesinde.</span><span class="sxs-lookup"><span data-stu-id="6b7d5-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="6b7d5-109">Aşağıdaki örnek, kullanımını gösterir. `<` işleci:</span><span class="sxs-lookup"><span data-stu-id="6b7d5-109">The following example demonstrates the usage of the `<` operator:</span></span>

[!code-csharp-interactive[less than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Less)]

## <a name="operator-overloadability"></a><span data-ttu-id="6b7d5-110">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="6b7d5-110">Operator overloadability</span></span>

<span data-ttu-id="6b7d5-111">Kullanıcı tanımlı türler için [aşırı](../keywords/operator.md) `<` işleci.</span><span class="sxs-lookup"><span data-stu-id="6b7d5-111">User-defined types can [overload](../keywords/operator.md) the `<` operator.</span></span> <span data-ttu-id="6b7d5-112">Bir tür "az" işleci aşırı `<`, ayrıca aşırı gerekir ["büyüktür" işleci](greater-than-operator.md) `>`.</span><span class="sxs-lookup"><span data-stu-id="6b7d5-112">If a type overloads the "less than" operator `<`, it must also overload the ["greater than" operator](greater-than-operator.md) `>`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6b7d5-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6b7d5-113">C# language specification</span></span>

<span data-ttu-id="6b7d5-114">Daha fazla bilgi için [ilişkisel ve tür testi işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6b7d5-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6b7d5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b7d5-115">See also</span></span>

- [<span data-ttu-id="6b7d5-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6b7d5-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6b7d5-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6b7d5-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6b7d5-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="6b7d5-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="6b7d5-119"><= İşleci</span><span class="sxs-lookup"><span data-stu-id="6b7d5-119"><= Operator</span></span>](less-than-equal-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
