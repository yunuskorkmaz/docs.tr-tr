---
title: temsilci işleci-C# başvurusu
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: f7cd7caf11d9f076a5d6e82aae696c914bd60e44
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916833"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="de714-102">Delegate işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="de714-102">delegate operator (C# reference)</span></span>

<span data-ttu-id="de714-103">`delegate`İşleci, bir temsilci türüne dönüştürülebilen anonim bir yöntem oluşturur:</span><span class="sxs-lookup"><span data-stu-id="de714-103">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](snippets/shared/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> <span data-ttu-id="de714-104">C# 3 ' ten başlayarak lambda ifadeleri anonim bir işlev oluşturmanın daha kısa ve açıklayıcı bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="de714-104">Beginning with C# 3, lambda expressions provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="de714-105">Lambda ifadesi oluşturmak için [=> işlecini](lambda-operator.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="de714-105">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>
>
> [!code-csharp-interactive[lambda expression](snippets/shared/DelegateOperator.cs#Lambda)]
>
> <span data-ttu-id="de714-106">Lambda ifadelerinin özellikleri hakkında daha fazla bilgi için örneğin, dış değişkenleri yakalama, bkz. [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="de714-106">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="de714-107">`delegate`İşlecini kullandığınızda parametre listesini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de714-107">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="de714-108">Bunu yaparsanız, oluşturulan anonim yöntem, aşağıdaki örnekte gösterildiği gibi, herhangi bir parametre listesiyle bir temsilci türüne dönüştürülebilir:</span><span class="sxs-lookup"><span data-stu-id="de714-108">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](snippets/shared/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="de714-109">Bu, lambda ifadeleri tarafından desteklenmeyen anonim yöntemlerin tek işlevsellikleridir.</span><span class="sxs-lookup"><span data-stu-id="de714-109">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="de714-110">Diğer tüm durumlarda, bir lambda ifadesi satır içi kod yazmak için tercih edilen bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="de714-110">In all other cases, a lambda expression is a preferred way to write inline code.</span></span>

<span data-ttu-id="de714-111">`delegate`Bir [temsilci türü](../builtin-types/reference-types.md#the-delegate-type)bildirmek için anahtar sözcüğünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de714-111">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="de714-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="de714-112">C# language specification</span></span>

<span data-ttu-id="de714-113">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="de714-113">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="de714-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de714-114">See also</span></span>

- [<span data-ttu-id="de714-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="de714-115">C# reference</span></span>](../index.md)
- [<span data-ttu-id="de714-116">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="de714-116">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="de714-117">=> işleci</span><span class="sxs-lookup"><span data-stu-id="de714-117">=> operator</span></span>](lambda-operator.md)
