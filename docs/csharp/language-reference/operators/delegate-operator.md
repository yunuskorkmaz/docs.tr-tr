---
title: temsilci operatörü - C# referansı
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1dd27fe5fdfdc1bc8a63e1298da00d252e800a72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847345"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="0d1e3-102">temsilci işleci (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="0d1e3-102">delegate operator (C# reference)</span></span>

<span data-ttu-id="0d1e3-103">İşleç, `delegate` temsilci türüne dönüştürülebilecek anonim bir yöntem oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0d1e3-103">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](snippets/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> <span data-ttu-id="0d1e3-104">C# 3 ile başlayarak lambda ifadeleri anonim bir işlev oluşturmak için daha kısa ve anlamlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d1e3-104">Beginning with C# 3, lambda expressions provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="0d1e3-105">Lambda ifadesini oluşturmak için [=> işleci](lambda-operator.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="0d1e3-105">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>
>
> [!code-csharp-interactive[lambda expression](snippets/DelegateOperator.cs#Lambda)]
>
> <span data-ttu-id="0d1e3-106">Lambda ifadelerinin özellikleri hakkında daha fazla bilgi için, örneğin, dış değişkenleri yakalama, [Lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0d1e3-106">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="0d1e3-107">İşleç `delegate` kullandığınızda, parametre listesini atlaabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d1e3-107">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="0d1e3-108">Bunu yaparsanız, oluşturulan anonim yöntem, aşağıdaki örnekte görüldüğü gibi, herhangi bir parametre listesi içeren bir temsilci türüne dönüştürülebilir:</span><span class="sxs-lookup"><span data-stu-id="0d1e3-108">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](snippets/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="0d1e3-109">Lambda ifadeleri tarafından desteklenmeyen anonim yöntemlerin tek işlevselliği bu.</span><span class="sxs-lookup"><span data-stu-id="0d1e3-109">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="0d1e3-110">Diğer tüm durumlarda, lambda ifadesi satır içinde kod yazmak için tercih edilen bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="0d1e3-110">In all other cases, a lambda expression is a preferred way to write inline code.</span></span>

<span data-ttu-id="0d1e3-111">Ayrıca bir `delegate` [temsilci türü](../builtin-types/reference-types.md#the-delegate-type)bildirmek için anahtar kelime kullanın.</span><span class="sxs-lookup"><span data-stu-id="0d1e3-111">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0d1e3-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0d1e3-112">C# language specification</span></span>

<span data-ttu-id="0d1e3-113">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0d1e3-113">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d1e3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d1e3-114">See also</span></span>

- [<span data-ttu-id="0d1e3-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0d1e3-115">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0d1e3-116">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="0d1e3-116">C# operators</span></span>](index.md)
- [<span data-ttu-id="0d1e3-117">=> operatörü</span><span class="sxs-lookup"><span data-stu-id="0d1e3-117">=> operator</span></span>](lambda-operator.md)
