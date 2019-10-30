---
title: varsayılan işleç- C# başvuru
ms.custom: seodec18
description: Bir türün varsayılan değerini oluşturmak için varsayılan işleci kullanın
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 6503e82a42f116a7ba8461ae060592377579f255
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039057"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="15695-103">Default işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="15695-103">default operator (C# reference)</span></span>

<span data-ttu-id="15695-104">`default` işleci, bir türün [varsayılan değerini](../keywords/default-values-table.md) üretir.</span><span class="sxs-lookup"><span data-stu-id="15695-104">The `default` operator produces the [default value](../keywords/default-values-table.md) of a type.</span></span> <span data-ttu-id="15695-105">`default` işlecinin bağımsız değişkeni bir türün veya tür parametresinin adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="15695-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="15695-106">Aşağıdaki örnek `default` işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="15695-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="15695-107">Ayrıca, bir [`switch` ifadesinde](../keywords/switch.md)varsayılan Case etiketi olarak `default` anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="15695-107">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="15695-108">Varsayılan sabit değer</span><span class="sxs-lookup"><span data-stu-id="15695-108">default literal</span></span>

<span data-ttu-id="15695-109">7,1 ' C# den başlayarak, derleyici ifade türünü çıkarsdığı zaman bir türün varsayılan değerini oluşturmak için`default`değişmez değerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15695-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="15695-110">`default` değişmez ifadesi, `T` çıkarılan tür olduğu `default(T)` ifadesiyle aynı değeri üretir.</span><span class="sxs-lookup"><span data-stu-id="15695-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="15695-111">`default` değişmez değerini aşağıdaki durumlardan herhangi birinde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="15695-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="15695-112">Bir değişkenin atamasında veya başlatılmasında.</span><span class="sxs-lookup"><span data-stu-id="15695-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="15695-113">[İsteğe bağlı bir yöntem parametresi](../../methods.md#optional-parameters-and-arguments)için varsayılan değer bildiriminde.</span><span class="sxs-lookup"><span data-stu-id="15695-113">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="15695-114">Bir bağımsız değişken değeri sağlamak için bir yöntem çağrısında.</span><span class="sxs-lookup"><span data-stu-id="15695-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="15695-115">Bir [`return` deyiminde](../keywords/return.md) veya [ifade-Bodied üye](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)içindeki bir ifade olarak.</span><span class="sxs-lookup"><span data-stu-id="15695-115">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="15695-116">Aşağıdaki örnek `default` değişmez değerinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="15695-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="15695-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="15695-117">C# language specification</span></span>

<span data-ttu-id="15695-118">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [varsayılan değer ifadeleri](~/_csharplang/spec/expressions.md#default-value-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="15695-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="15695-119">`default` değişmez değeri hakkında daha fazla bilgi için bkz. [özellik teklifi notunun](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="15695-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15695-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15695-120">See also</span></span>

- [<span data-ttu-id="15695-121">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="15695-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="15695-122">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="15695-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="15695-123">Varsayılan değerler tablosu</span><span class="sxs-lookup"><span data-stu-id="15695-123">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="15695-124">.NET 'teki genel türler</span><span class="sxs-lookup"><span data-stu-id="15695-124">Generics in .NET</span></span>](../../../standard/generics/index.md)
