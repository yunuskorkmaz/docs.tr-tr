---
title: varsayılan işleç- C# başvuru
ms.custom: seodec18
description: Bir türün varsayılan değerini oluşturmak için varsayılan işleci kullanın
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 5623cb9dc3790b5bb99635c41cb3f122f4c71d8e
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68804240"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="d6454-103">Default işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="d6454-103">default operator (C# reference)</span></span>

<span data-ttu-id="d6454-104">İşleci bir türün [varsayılan değerini](../keywords/default-values-table.md) üretir. `default`</span><span class="sxs-lookup"><span data-stu-id="d6454-104">The `default` operator produces the [default value](../keywords/default-values-table.md) of a type.</span></span> <span data-ttu-id="d6454-105">`default` İşlecin bağımsız değişkeni bir türün veya tür parametresinin adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6454-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="d6454-106">Aşağıdaki örnek `default` işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="d6454-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="d6454-107">Ayrıca, `default` anahtar sözcüğünü [ `switch` deyimdeki](../keywords/switch.md)varsayılan Case etiketi olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6454-107">You also use the `default` keyword as the default case label within the [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="d6454-108">Varsayılan sabit değer</span><span class="sxs-lookup"><span data-stu-id="d6454-108">default literal</span></span>

<span data-ttu-id="d6454-109">7,1 ' C# den başlayarak, derleyicinin ifade türünü `default` çıkardığı zaman bir türün varsayılan değerini oluşturmak için değişmez değeri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6454-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="d6454-110">Değişmez değer ifadesi, çıkarılan tür `T` olan `default(T)` ifadesiyle aynı değeri üretir. `default`</span><span class="sxs-lookup"><span data-stu-id="d6454-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="d6454-111">Aşağıdaki durumlardan herhangi birinde `default` değişmez değeri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d6454-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="d6454-112">Bir değişkenin atamasında veya başlatılmasında.</span><span class="sxs-lookup"><span data-stu-id="d6454-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="d6454-113">İsteğe bağlı bir yöntem parametresi için varsayılan değer bildiriminde.</span><span class="sxs-lookup"><span data-stu-id="d6454-113">In the declaration of the default value for an optional method parameter.</span></span>
- <span data-ttu-id="d6454-114">Bir bağımsız değişken değeri sağlamak için bir yöntem çağrısında.</span><span class="sxs-lookup"><span data-stu-id="d6454-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="d6454-115">Bir `return` deyimde veya bir ifade ile ifade olarak ifade olarak.</span><span class="sxs-lookup"><span data-stu-id="d6454-115">In a `return` statement or as an expression in an expression-bodied member.</span></span>

<span data-ttu-id="d6454-116">Aşağıdaki örnek, `default` değişmez değerin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="d6454-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="d6454-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d6454-117">C# language specification</span></span>

<span data-ttu-id="d6454-118">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [varsayılan değer ifadeleri](~/_csharplang/spec/expressions.md#default-value-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d6454-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="d6454-119">`default` Değişmez değer hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="d6454-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d6454-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6454-120">See also</span></span>

- [<span data-ttu-id="d6454-121">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="d6454-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d6454-122">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="d6454-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="d6454-123">Varsayılan değerler tablosu</span><span class="sxs-lookup"><span data-stu-id="d6454-123">Default values table</span></span>](../keywords/default-values-table.md)
