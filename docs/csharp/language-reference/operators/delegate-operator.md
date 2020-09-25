---
description: temsilci işleci-C# başvurusu
title: temsilci işleci-C# başvurusu
ms.date: 09/25/2020
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: db2bf673db12e4a10741a26112820726a4b8aaee
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247663"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="1fec3-103">Delegate işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1fec3-103">delegate operator (C# reference)</span></span>

<span data-ttu-id="1fec3-104">`delegate`İşleci, bir temsilci türüne dönüştürülebilen anonim bir yöntem oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1fec3-104">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](snippets/shared/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> <span data-ttu-id="1fec3-105">C# 3 ' ten başlayarak lambda ifadeleri anonim bir işlev oluşturmanın daha kısa ve açıklayıcı bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fec3-105">Beginning with C# 3, lambda expressions provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="1fec3-106">Lambda ifadesi oluşturmak için [=> işlecini](lambda-operator.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="1fec3-106">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>
>
> [!code-csharp-interactive[lambda expression](snippets/shared/DelegateOperator.cs#Lambda)]
>
> <span data-ttu-id="1fec3-107">Lambda ifadelerinin özellikleri hakkında daha fazla bilgi için örneğin, dış değişkenleri yakalama, bkz. [lambda ifadeleri](lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1fec3-107">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](lambda-expressions.md).</span></span>

<span data-ttu-id="1fec3-108">`delegate`İşlecini kullandığınızda parametre listesini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fec3-108">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="1fec3-109">Bunu yaparsanız, oluşturulan anonim yöntem, aşağıdaki örnekte gösterildiği gibi, herhangi bir parametre listesiyle bir temsilci türüne dönüştürülebilir:</span><span class="sxs-lookup"><span data-stu-id="1fec3-109">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](snippets/shared/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="1fec3-110">Bu, lambda ifadeleri tarafından desteklenmeyen anonim yöntemlerin tek işlevsellikleridir.</span><span class="sxs-lookup"><span data-stu-id="1fec3-110">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="1fec3-111">Diğer tüm durumlarda, bir lambda ifadesi satır içi kod yazmak için tercih edilen bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="1fec3-111">In all other cases, a lambda expression is a preferred way to write inline code.</span></span>

<span data-ttu-id="1fec3-112">C# 9,0 ile başlayarak, yöntemi tarafından kullanılmayan anonim bir yöntemin iki veya daha fazla giriş parametresini belirtmek için [atarsa](../../discards.md) ' u kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1fec3-112">Beginning with C# 9.0, you can use [discards](../../discards.md) to specify two or more input parameters of an anonymous method that aren't used by the method:</span></span>

:::code language="csharp" source="snippets/shared/DelegateOperator.cs" id="SnippetDiscards" :::

<span data-ttu-id="1fec3-113">Geriye dönük uyumluluk için, yalnızca tek bir parametre adlandırılmışsa `_` , `_` anonim bir yöntemde bu parametrenin adı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1fec3-113">For backwards compatibility, if only a single parameter is named `_`, `_` is treated as the name of that parameter within an anonymous method.</span></span>

<span data-ttu-id="1fec3-114">C# 9,0 ' den itibaren, `static` anonim bir yöntemin bildiriminde değiştiricisini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1fec3-114">Also beginning with C# 9.0, you can use the `static` modifier at the declaration of an anonymous method:</span></span>

:::code language="csharp" source="snippets/shared/DelegateOperator.cs" id="SnippetStatic" :::

<span data-ttu-id="1fec3-115">Statik anonim bir yöntem, kapsayan kapsamlardan yerel değişkenleri veya örnek durumunu yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="1fec3-115">A static anonymous method can't capture local variables or instance state from enclosing scopes.</span></span>

<span data-ttu-id="1fec3-116">`delegate`Bir [temsilci türü](../builtin-types/reference-types.md#the-delegate-type)bildirmek için anahtar sözcüğünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fec3-116">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1fec3-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1fec3-117">C# language specification</span></span>

<span data-ttu-id="1fec3-118">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1fec3-118">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1fec3-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fec3-119">See also</span></span>

- [<span data-ttu-id="1fec3-120">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1fec3-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1fec3-121">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="1fec3-121">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="1fec3-122">=> işleci</span><span class="sxs-lookup"><span data-stu-id="1fec3-122">=> operator</span></span>](lambda-operator.md)
