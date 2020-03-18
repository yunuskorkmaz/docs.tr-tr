---
title: bool tipi - C# referans
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 2ba2e54a6b0f24402fc3728dfe19b548a2368830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846451"
---
# <a name="bool-c-reference"></a><span data-ttu-id="cf3e1-102">bool (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="cf3e1-102">bool (C# reference)</span></span>

<span data-ttu-id="cf3e1-103">Tür `bool` anahtar kelimesi,.NET <xref:System.Boolean?displayProperty=nameWithType> yapı türüiçin boolean değerini temsil eden bir `true` diğer `false`addır ve bu da .</span><span class="sxs-lookup"><span data-stu-id="cf3e1-103">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="cf3e1-104">`bool` Mantıksal işlemleri türünün değerleriyle gerçekleştirmek için [Boolean mantıksal](../operators/boolean-logical-operators.md) işleçlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-104">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="cf3e1-105">Tür, `bool` [karşılaştırma](../operators/comparison-operators.md) ve [eşitlik](../operators/equality-operators.md) işleçlerinin sonuç türüdür.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-105">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="cf3e1-106">Bir `bool` ifade [if,](../keywords/if-else.md) [do](../keywords/do.md), [while](../keywords/while.md), ve ifadeler [için](../keywords/for.md) ve [ `?:`koşullu işleç ](../operators/conditional-operator.md)bir kontrol koşullu ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-106">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="cf3e1-107">`bool` Türünün varsayılan `false`değeri.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-107">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="cf3e1-108">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="cf3e1-108">Literals</span></span>

<span data-ttu-id="cf3e1-109">Bir `bool` değişkeni `true` `false` başlatmak veya bir `bool` değeri geçirmek için ve literals'i kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cf3e1-109">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="cf3e1-110">Üç değerli Boolean mantığı</span><span class="sxs-lookup"><span data-stu-id="cf3e1-110">Three-valued Boolean logic</span></span>

<span data-ttu-id="cf3e1-111">Örneğin, üç `bool?` değerli Boolean türünü destekleyen veritabanlarıyla çalışırken, üç değerli mantığı desteklemeniz gerekiyorsa, nullable türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-111">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="cf3e1-112">`bool?` Operands için, önceden `&` tanımlanmış `|` ve operatörler üç değerli mantığı destekler.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-112">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="cf3e1-113">Daha fazla bilgi için [Boolean mantıksal işleçleri](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçleri](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-113">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="cf3e1-114">Nullable değer türleri hakkında daha fazla bilgi için, [Nullable değer türleri](nullable-value-types.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-114">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="cf3e1-115">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="cf3e1-115">Conversions</span></span>

<span data-ttu-id="cf3e1-116">C# `bool` türü içeren yalnızca iki dönüşüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-116">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="cf3e1-117">Bunlar, karşılık gelen geçersiz `bool?` türüne örtülü bir dönüştürme `bool?` ve türden açık bir dönüştürmedir.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-117">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="cf3e1-118">Ancak,.NET, `bool` türe dönüştürmek için kullanabileceğiniz ek yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-118">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="cf3e1-119">Daha fazla bilgi için API başvuru sayfasının [Boolean değerleri bölümüne dönüştürme ve](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) değiştirme bölümüne <xref:System.Boolean?displayProperty=nameWithType> bakın.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-119">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cf3e1-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="cf3e1-120">C# language specification</span></span>

<span data-ttu-id="cf3e1-121">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [bool türü](~/_csharplang/spec/types.md#the-bool-type) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-121">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf3e1-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf3e1-122">See also</span></span>

- [<span data-ttu-id="cf3e1-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="cf3e1-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cf3e1-124">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="cf3e1-124">Value types</span></span>](value-types.md)
- [<span data-ttu-id="cf3e1-125">true ve false işleçleri</span><span class="sxs-lookup"><span data-stu-id="cf3e1-125">true and false operators</span></span>](../operators/true-false-operators.md)
