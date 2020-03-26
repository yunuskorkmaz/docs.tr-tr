---
title: varsayılan değer ifadeleri - C# başvurusu
description: Bir türün varsayılan değerini elde etmek için varsayılan değer ifadelerini kullanma
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
- default
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 2adfd8d24066e9dad50c3c18407d3ade71b4b68e
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507184"
---
# <a name="default-value-expressions-c-reference"></a><span data-ttu-id="7b6aa-103">varsayılan değer ifadeleri (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7b6aa-103">default value expressions (C# reference)</span></span>

<span data-ttu-id="7b6aa-104">Varsayılan değer ifadesi, bir türün [varsayılan değerini](../builtin-types/default-values.md) üretir.</span><span class="sxs-lookup"><span data-stu-id="7b6aa-104">A default value expression produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="7b6aa-105">İki tür varsayılan değer ifadesi vardır: [varsayılan işleç](#default-operator) çağrısı ve [varsayılan bir literal](#default-literal).</span><span class="sxs-lookup"><span data-stu-id="7b6aa-105">There are two kinds of default value expressions: the [default operator](#default-operator) call and a [default literal](#default-literal).</span></span>

<span data-ttu-id="7b6aa-106">`default` Ayrıca bir [ `switch` deyim](../keywords/switch.md)içinde varsayılan durum etiketi olarak anahtar kelime kullanın.</span><span class="sxs-lookup"><span data-stu-id="7b6aa-106">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-operator"></a><span data-ttu-id="7b6aa-107">default işleçi</span><span class="sxs-lookup"><span data-stu-id="7b6aa-107">default operator</span></span>

<span data-ttu-id="7b6aa-108">Aşağıdaki örnekte `default` görüldüğü gibi, işlecibağımsız değişkenbir tür veya tür parametresi adı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="7b6aa-108">The argument to the `default` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a><span data-ttu-id="7b6aa-109">varsayılan edebi</span><span class="sxs-lookup"><span data-stu-id="7b6aa-109">default literal</span></span>

<span data-ttu-id="7b6aa-110">C# 7.1 ile başlayarak, `default` derleyici ifade türünü çıkarabildiği bir türün varsayılan değerini üretmek için literal'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b6aa-110">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="7b6aa-111">Literal `default` ifade, çıkarılan türdeki `default(T)` ifadeyle `T` aynı değeri üretir.</span><span class="sxs-lookup"><span data-stu-id="7b6aa-111">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="7b6aa-112">Aşağıdaki durumlardan `default` herhangi birinde gerçek kullanımı yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7b6aa-112">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="7b6aa-113">Bir değişkenin atamasında veya başlatılmasında.</span><span class="sxs-lookup"><span data-stu-id="7b6aa-113">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="7b6aa-114">İsteğe bağlı yöntem [parametresi](../../methods.md#optional-parameters-and-arguments)için varsayılan değer bildiriminde .</span><span class="sxs-lookup"><span data-stu-id="7b6aa-114">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="7b6aa-115">Bir yöntemde bir bağımsız değişken değeri sağlamak için çağrı.</span><span class="sxs-lookup"><span data-stu-id="7b6aa-115">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="7b6aa-116">[ `return` İfade](../keywords/return.md) de veya [ifade gövdeli](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)bir üyede ifade olarak .</span><span class="sxs-lookup"><span data-stu-id="7b6aa-116">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="7b6aa-117">Aşağıdaki `default` örnek, edebi kullanımı gösterir:</span><span class="sxs-lookup"><span data-stu-id="7b6aa-117">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="7b6aa-118">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7b6aa-118">C# language specification</span></span>

<span data-ttu-id="7b6aa-119">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Varsayılan değer ifadeleri](~/_csharplang/spec/expressions.md#default-value-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7b6aa-119">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="7b6aa-120">`default` Gerçek hakkında daha fazla bilgi için özellik teklifi [notuna](~/_csharplang/proposals/csharp-7.1/target-typed-default.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="7b6aa-120">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7b6aa-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b6aa-121">See also</span></span>

- [<span data-ttu-id="7b6aa-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7b6aa-122">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7b6aa-123">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="7b6aa-123">C# operators</span></span>](index.md)
- [<span data-ttu-id="7b6aa-124">C# türlerinin varsayılan değerleri</span><span class="sxs-lookup"><span data-stu-id="7b6aa-124">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="7b6aa-125">.NET içindeki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="7b6aa-125">Generics in .NET</span></span>](../../../standard/generics/index.md)
