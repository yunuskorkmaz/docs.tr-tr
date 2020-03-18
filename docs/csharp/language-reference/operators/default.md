---
title: varsayılan işleç - C# referans
description: Bir türün varsayılan değerini üretmek için varsayılan işleci kullanma
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 0d37fe952e71e74f014872231a2e58663dea9d18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399485"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="90f97-103">varsayılan işleç (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="90f97-103">default operator (C# reference)</span></span>

<span data-ttu-id="90f97-104">İşleç `default` bir türün [varsayılan değerini](../builtin-types/default-values.md) üretir.</span><span class="sxs-lookup"><span data-stu-id="90f97-104">The `default` operator produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="90f97-105">Işleci için `default` bağımsız değişken bir tür veya tür parametresi adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="90f97-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="90f97-106">Aşağıdaki örnek, işleç `default` kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="90f97-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="90f97-107">`default` Ayrıca bir [ `switch` deyim](../keywords/switch.md)içinde varsayılan durum etiketi olarak anahtar kelime kullanın.</span><span class="sxs-lookup"><span data-stu-id="90f97-107">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="90f97-108">varsayılan edebi</span><span class="sxs-lookup"><span data-stu-id="90f97-108">default literal</span></span>

<span data-ttu-id="90f97-109">C# 7.1 ile başlayarak, `default` derleyici ifade türünü çıkarabildiği bir türün varsayılan değerini üretmek için literal'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90f97-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="90f97-110">Literal `default` ifade, çıkarılan türdeki `default(T)` ifadeyle `T` aynı değeri üretir.</span><span class="sxs-lookup"><span data-stu-id="90f97-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="90f97-111">Aşağıdaki durumlardan `default` herhangi birinde gerçek kullanımı yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="90f97-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="90f97-112">Bir değişkenin atamasında veya başlatılmasında.</span><span class="sxs-lookup"><span data-stu-id="90f97-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="90f97-113">İsteğe bağlı yöntem [parametresi](../../methods.md#optional-parameters-and-arguments)için varsayılan değer bildiriminde .</span><span class="sxs-lookup"><span data-stu-id="90f97-113">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="90f97-114">Bir yöntemde bir bağımsız değişken değeri sağlamak için çağrı.</span><span class="sxs-lookup"><span data-stu-id="90f97-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="90f97-115">[ `return` İfade](../keywords/return.md) de veya [ifade gövdeli](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)bir üyede ifade olarak .</span><span class="sxs-lookup"><span data-stu-id="90f97-115">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="90f97-116">Aşağıdaki `default` örnek, edebi kullanımı gösterir:</span><span class="sxs-lookup"><span data-stu-id="90f97-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="90f97-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="90f97-117">C# language specification</span></span>

<span data-ttu-id="90f97-118">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Varsayılan değer ifadeleri](~/_csharplang/spec/expressions.md#default-value-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="90f97-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="90f97-119">`default` Gerçek hakkında daha fazla bilgi için özellik teklifi [notuna](~/_csharplang/proposals/csharp-7.1/target-typed-default.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="90f97-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="90f97-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90f97-120">See also</span></span>

- [<span data-ttu-id="90f97-121">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="90f97-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="90f97-122">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="90f97-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="90f97-123">C# türlerinin varsayılan değerleri</span><span class="sxs-lookup"><span data-stu-id="90f97-123">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="90f97-124">.NET içindeki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="90f97-124">Generics in .NET</span></span>](../../../standard/generics/index.md)
