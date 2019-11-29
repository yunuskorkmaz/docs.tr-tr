---
title: bool türü- C# başvuru
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 1e79de6d9e5cf973ce394bfb06871777c562c8ac
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74553039"
---
# <a name="bool-c-reference"></a><span data-ttu-id="7ff02-102">bool (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="7ff02-102">bool (C# reference)</span></span>

<span data-ttu-id="7ff02-103">`bool` Type anahtar sözcüğü, `true` veya `false`olabilen bir Boolean değeri temsil eden .NET <xref:System.Boolean?displayProperty=nameWithType> yapı türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="7ff02-103">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="7ff02-104">`bool` türünün değerleriyle mantıksal işlemler gerçekleştirmek için, [Boolean mantıksal](../operators/boolean-logical-operators.md) işleçler kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ff02-104">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="7ff02-105">`bool` türü [karşılaştırma](../operators/comparison-operators.md) ve [eşitlik](../operators/equality-operators.md) işleçlerinin sonuç türüdür.</span><span class="sxs-lookup"><span data-stu-id="7ff02-105">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="7ff02-106">`bool` ifade, [IF](../keywords/if-else.md), [Do](../keywords/do.md), [while](../keywords/while.md)ve [for](../keywords/for.md) deyimlerinde ve [koşullu işleç `?:`](../operators/conditional-operator.md)bir denetim koşullu ifadesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ff02-106">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="7ff02-107">`bool` türünün varsayılan değeri `false`.</span><span class="sxs-lookup"><span data-stu-id="7ff02-107">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="7ff02-108">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="7ff02-108">Literals</span></span>

<span data-ttu-id="7ff02-109">`bool` değişkenini başlatmak veya bir `bool` değeri geçirmek için `true` ve `false` değişmez değerleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7ff02-109">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](~/samples/csharp/language-reference/builtin-types/BoolType.cs#Literals)]

## <a name="conversions"></a><span data-ttu-id="7ff02-110">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="7ff02-110">Conversions</span></span>

<span data-ttu-id="7ff02-111">C#`bool` türünü içeren yalnızca iki dönüştürme sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ff02-111">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="7ff02-112">Bunlar, karşılık gelen null yapılabilir `bool?` türüne örtülü bir dönüşümtür ve `bool?` türünden açık bir dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="7ff02-112">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="7ff02-113">Ancak, .NET `bool` türüne dönüştürmek için kullanabileceğiniz ek yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ff02-113">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="7ff02-114">Daha fazla bilgi için, <xref:System.Boolean?displayProperty=nameWithType> API başvurusu sayfasının [Boole değerlerine dönüştürme](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7ff02-114">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="7ff02-115">Üç değerli Boole mantığı</span><span class="sxs-lookup"><span data-stu-id="7ff02-115">Three-valued Boolean logic</span></span>

<span data-ttu-id="7ff02-116">Üç değerli mantığı desteketmeniz gerekiyorsa (örneğin, üç değerli bir Boolean türünü destekleyen veritabanlarıyla çalışırken) null yapılabilir `bool?` türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ff02-116">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="7ff02-117">`bool?` işlenenleri için, önceden tanımlanmış `&` ve `|` işleçleri üç değerli mantığı destekler.</span><span class="sxs-lookup"><span data-stu-id="7ff02-117">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="7ff02-118">Daha fazla bilgi için, [Boole mantıksal işleçler](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7ff02-118">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="7ff02-119">Null yapılabilir değer türleri hakkında daha fazla bilgi için bkz. [Nullable değer türleri](nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="7ff02-119">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7ff02-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7ff02-120">C# language specification</span></span>

<span data-ttu-id="7ff02-121">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [bool türü](~/_csharplang/spec/types.md#the-bool-type) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7ff02-121">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7ff02-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ff02-122">See also</span></span>

- [<span data-ttu-id="7ff02-123">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="7ff02-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7ff02-124">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="7ff02-124">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="7ff02-125">true ve false işleçleri</span><span class="sxs-lookup"><span data-stu-id="7ff02-125">true and false operators</span></span>](../operators/true-false-operators.md)
