---
title: bool türü-C# başvurusu
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
- "true"
- "false"
- true_CSharpKeyword
- false_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 4623dc7d6c8c6c437c78aee45f0eeee8a92e3200
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854886"
---
# <a name="bool-c-reference"></a><span data-ttu-id="df6fa-102">bool (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="df6fa-102">bool (C# reference)</span></span>

<span data-ttu-id="df6fa-103">`bool`Type anahtar sözcüğü, <xref:System.Boolean?displayProperty=nameWithType> ya da olabilen bir Boole değerini temsil eden .net yapı türü için bir diğer addır `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="df6fa-103">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="df6fa-104">Tür değerleriyle mantıksal işlemler gerçekleştirmek için `bool` [Boolean mantıksal](../operators/boolean-logical-operators.md) işleçler kullanın.</span><span class="sxs-lookup"><span data-stu-id="df6fa-104">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="df6fa-105">`bool`Tür, [karşılaştırma](../operators/comparison-operators.md) ve [eşitlik](../operators/equality-operators.md) işleçlerinin sonuç türüdür.</span><span class="sxs-lookup"><span data-stu-id="df6fa-105">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="df6fa-106">Bir `bool` ifade, [IF](../keywords/if-else.md), [Do](../keywords/do.md), [while](../keywords/while.md)ve [for](../keywords/for.md) deyimlerinde ve [koşullu işleçte `?:` ](../operators/conditional-operator.md)bir denetim koşullu ifadesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="df6fa-106">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="df6fa-107">Türün varsayılan değeri `bool` `false` .</span><span class="sxs-lookup"><span data-stu-id="df6fa-107">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="df6fa-108">Değişmez Değerler</span><span class="sxs-lookup"><span data-stu-id="df6fa-108">Literals</span></span>

<span data-ttu-id="df6fa-109">`true` `false` Bir `bool` değişkeni başlatmak veya bir değeri geçirmek için ve değişmez `bool` değerlerini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df6fa-109">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="df6fa-110">Üç değerli Boole mantığı</span><span class="sxs-lookup"><span data-stu-id="df6fa-110">Three-valued Boolean logic</span></span>

<span data-ttu-id="df6fa-111">Üç `bool?` değerli mantığı desteketmeniz gerekiyorsa (örneğin, üç değerli bir Boolean türünü destekleyen veritabanlarıyla çalışırken), null yapılabilir türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="df6fa-111">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="df6fa-112">İşlenenler için `bool?` , önceden tanımlanmış `&` ve `|` işleçleri üç değerli mantığı destekler.</span><span class="sxs-lookup"><span data-stu-id="df6fa-112">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="df6fa-113">Daha fazla bilgi için, [Boole mantıksal işleçler](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="df6fa-113">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="df6fa-114">Null yapılabilir değer türleri hakkında daha fazla bilgi için bkz. [Nullable değer türleri](nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="df6fa-114">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="df6fa-115">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="df6fa-115">Conversions</span></span>

<span data-ttu-id="df6fa-116">C# yalnızca türü içeren iki dönüştürme sağlar `bool` .</span><span class="sxs-lookup"><span data-stu-id="df6fa-116">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="df6fa-117">Bunlar, karşılık gelen null yapılabilir `bool?` türe ve türden açık dönüştürmeye örtülü bir dönüşümtür `bool?` .</span><span class="sxs-lookup"><span data-stu-id="df6fa-117">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="df6fa-118">Ancak, .NET, türden veya türünden dönüştürmek için kullanabileceğiniz ek yöntemler sağlar `bool` .</span><span class="sxs-lookup"><span data-stu-id="df6fa-118">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="df6fa-119">Daha fazla bilgi için, API başvurusu sayfasının [Boole değerlerine dönüştürme](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) bölümüne bakın <xref:System.Boolean?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="df6fa-119">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="df6fa-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="df6fa-120">C# language specification</span></span>

<span data-ttu-id="df6fa-121">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [bool türü](~/_csharplang/spec/types.md#the-bool-type) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="df6fa-121">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df6fa-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df6fa-122">See also</span></span>

- [<span data-ttu-id="df6fa-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="df6fa-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="df6fa-124">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="df6fa-124">Value types</span></span>](value-types.md)
- [<span data-ttu-id="df6fa-125">true ve false işleçleri</span><span class="sxs-lookup"><span data-stu-id="df6fa-125">true and false operators</span></span>](../operators/true-false-operators.md)
