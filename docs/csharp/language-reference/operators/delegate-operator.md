---
description: temsilci işleci-C# başvurusu
title: temsilci işleci-C# başvurusu
ms.date: 09/22/2020
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 6c087d9bdb2f526cf7d94c3a0f2c1a929b0343ef
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874917"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="2eb32-103">Delegate işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2eb32-103">delegate operator (C# reference)</span></span>

<span data-ttu-id="2eb32-104">`delegate`İşleci, bir temsilci türüne dönüştürülebilen anonim bir yöntem oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2eb32-104">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](snippets/shared/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> <span data-ttu-id="2eb32-105">C# 3 ' ten başlayarak lambda ifadeleri anonim bir işlev oluşturmanın daha kısa ve açıklayıcı bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="2eb32-105">Beginning with C# 3, lambda expressions provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="2eb32-106">Lambda ifadesi oluşturmak için [=> işlecini](lambda-operator.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="2eb32-106">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>
>
> [!code-csharp-interactive[lambda expression](snippets/shared/DelegateOperator.cs#Lambda)]
>
> <span data-ttu-id="2eb32-107">Lambda ifadelerinin özellikleri hakkında daha fazla bilgi için örneğin, dış değişkenleri yakalama, bkz. [lambda ifadeleri](lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2eb32-107">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](lambda-expressions.md).</span></span>

<span data-ttu-id="2eb32-108">`delegate`İşlecini kullandığınızda parametre listesini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2eb32-108">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="2eb32-109">Bunu yaparsanız, oluşturulan anonim yöntem, aşağıdaki örnekte gösterildiği gibi, herhangi bir parametre listesiyle bir temsilci türüne dönüştürülebilir:</span><span class="sxs-lookup"><span data-stu-id="2eb32-109">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](snippets/shared/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="2eb32-110">Bu, lambda ifadeleri tarafından desteklenmeyen anonim yöntemlerin tek işlevsellikleridir.</span><span class="sxs-lookup"><span data-stu-id="2eb32-110">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="2eb32-111">Diğer tüm durumlarda, bir lambda ifadesi satır içi kod yazmak için tercih edilen bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="2eb32-111">In all other cases, a lambda expression is a preferred way to write inline code.</span></span>

<span data-ttu-id="2eb32-112">C# 9,0 ile başlayarak, yöntemi tarafından kullanılmayan anonim bir yöntemin iki veya daha fazla giriş parametresini belirtmek için [atarsa](../../discards.md) ' u kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2eb32-112">Beginning with C# 9.0, you can use [discards](../../discards.md) to specify two or more input parameters of an anonymous method that aren't used by the method:</span></span>

:::code language="csharp" source="snippets/shared/DelegateOperator.cs" id="SnippetDiscards" :::

<span data-ttu-id="2eb32-113">Geriye dönük uyumluluk için, yalnızca tek bir parametre adlandırılmışsa `_` , `_` anonim bir yöntemde bu parametrenin adı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2eb32-113">For backwards compatibility, if only a single parameter is named `_`, `_` is treated as the name of that parameter within an anonymous method.</span></span>

<span data-ttu-id="2eb32-114">`delegate`Bir [temsilci türü](../builtin-types/reference-types.md#the-delegate-type)bildirmek için anahtar sözcüğünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2eb32-114">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2eb32-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="2eb32-115">C# language specification</span></span>

<span data-ttu-id="2eb32-116">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2eb32-116">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2eb32-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2eb32-117">See also</span></span>

- [<span data-ttu-id="2eb32-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2eb32-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2eb32-119">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="2eb32-119">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="2eb32-120">=> işleci</span><span class="sxs-lookup"><span data-stu-id="2eb32-120">=> operator</span></span>](lambda-operator.md)
