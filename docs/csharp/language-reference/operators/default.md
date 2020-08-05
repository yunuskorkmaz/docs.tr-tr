---
title: Varsayılan değer ifadeleri-C# başvurusu
description: Bir türün varsayılan değerini elde etmek için varsayılan değer ifadelerini kullanın
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
- default
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: c07eb8e50dc2ec3413882fa841d2f896b28d2e8d
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556715"
---
# <a name="default-value-expressions-c-reference"></a><span data-ttu-id="c3d1f-103">Varsayılan değer ifadeleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c3d1f-103">default value expressions (C# reference)</span></span>

<span data-ttu-id="c3d1f-104">Varsayılan değer ifadesi bir türün [varsayılan değerini](../builtin-types/default-values.md) üretir.</span><span class="sxs-lookup"><span data-stu-id="c3d1f-104">A default value expression produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="c3d1f-105">İki tür varsayılan değer ifadesi vardır: [varsayılan işleç](#default-operator) çağrısı ve [varsayılan bir sabit](#default-literal)değer.</span><span class="sxs-lookup"><span data-stu-id="c3d1f-105">There are two kinds of default value expressions: the [default operator](#default-operator) call and a [default literal](#default-literal).</span></span>

<span data-ttu-id="c3d1f-106">Ayrıca, `default` anahtar sözcüğünü bir [ `switch` deyimindeki](../keywords/switch.md)varsayılan Case etiketi olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3d1f-106">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-operator"></a><span data-ttu-id="c3d1f-107">default işleçi</span><span class="sxs-lookup"><span data-stu-id="c3d1f-107">default operator</span></span>

<span data-ttu-id="c3d1f-108">`default`Aşağıdaki örnekte gösterildiği gibi, işlecin bağımsız değişkeni bir tür veya tür parametresinin adı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="c3d1f-108">The argument to the `default` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a><span data-ttu-id="c3d1f-109">Varsayılan sabit değer</span><span class="sxs-lookup"><span data-stu-id="c3d1f-109">default literal</span></span>

<span data-ttu-id="c3d1f-110">C# 7,1 ' den başlayarak, `default` derleyicinin ifade türünü çıkardığı zaman bir türün varsayılan değerini oluşturmak için değişmez değeri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3d1f-110">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="c3d1f-111">`default`Değişmez değer ifadesi, `default(T)` çıkarılan tür olan ifadesiyle aynı değeri üretir `T` .</span><span class="sxs-lookup"><span data-stu-id="c3d1f-111">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="c3d1f-112">`default`Aşağıdaki durumlardan herhangi birinde değişmez değeri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c3d1f-112">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="c3d1f-113">Bir değişkenin atamasında veya başlatılmasında.</span><span class="sxs-lookup"><span data-stu-id="c3d1f-113">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="c3d1f-114">[İsteğe bağlı bir yöntem parametresi](../../methods.md#optional-parameters-and-arguments)için varsayılan değer bildiriminde.</span><span class="sxs-lookup"><span data-stu-id="c3d1f-114">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="c3d1f-115">Bir bağımsız değişken değeri sağlamak için bir yöntem çağrısında.</span><span class="sxs-lookup"><span data-stu-id="c3d1f-115">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="c3d1f-116">Bir deyimde [ `return` veya bir](../keywords/return.md) [ifade ile](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)ifade olarak ifade olarak.</span><span class="sxs-lookup"><span data-stu-id="c3d1f-116">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="c3d1f-117">Aşağıdaki örnek, `default` değişmez değerin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="c3d1f-117">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="c3d1f-118">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c3d1f-118">C# language specification</span></span>

<span data-ttu-id="c3d1f-119">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [varsayılan değer ifadeleri](~/_csharplang/spec/expressions.md#default-value-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c3d1f-119">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="c3d1f-120">Değişmez değer hakkında daha fazla bilgi için `default` bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="c3d1f-120">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3d1f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3d1f-121">See also</span></span>

- [<span data-ttu-id="c3d1f-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c3d1f-122">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c3d1f-123">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="c3d1f-123">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="c3d1f-124">C# türlerinin varsayılan değerleri</span><span class="sxs-lookup"><span data-stu-id="c3d1f-124">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="c3d1f-125">.NET içindeki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="c3d1f-125">Generics in .NET</span></span>](../../../standard/generics/index.md)
