---
description: New kısıtlaması-C# başvurusu
title: New kısıtlaması-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: f7b097729fe973aba7b85c48e1b1033aade83080
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139456"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="8d2cc-103">New kısıtlaması (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8d2cc-103">new constraint (C# Reference)</span></span>

<span data-ttu-id="8d2cc-104">`new`Kısıtlama, genel sınıf bildirimindeki bir tür bağımsız değişkeninin Ortak parametresiz bir oluşturucuya sahip olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d2cc-104">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="8d2cc-105">Kısıtlamayı kullanmak için `new` tür soyut olamaz.</span><span class="sxs-lookup"><span data-stu-id="8d2cc-105">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="8d2cc-106">`new`Aşağıdaki örnekte gösterildiği gibi, genel bir sınıf türün yeni örneklerini oluşturduğunda, kısıtlamayı bir tür parametresine uygulayın:</span><span class="sxs-lookup"><span data-stu-id="8d2cc-106">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="8d2cc-107">`new()`Kısıtlamayı diğer kısıtlamalarla birlikte kullandığınızda, en son belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="8d2cc-107">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="8d2cc-108">Daha fazla bilgi için bkz. [tür parametrelerindeki kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8d2cc-108">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="8d2cc-109">`new`Anahtar sözcüğünü, [bir tür örneği](../operators/new-operator.md) veya bir [üye bildirimi değiştiricisi](new-modifier.md)olarak oluşturmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d2cc-109">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8d2cc-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8d2cc-110">C# language specification</span></span>

<span data-ttu-id="8d2cc-111">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [tür parametresi kısıtlamaları](~/_csharplang/spec/classes.md#type-parameter-constraints) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8d2cc-111">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d2cc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d2cc-112">See also</span></span>

- [<span data-ttu-id="8d2cc-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8d2cc-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8d2cc-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8d2cc-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8d2cc-115">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8d2cc-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8d2cc-116">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="8d2cc-116">Generics</span></span>](../../programming-guide/generics/index.md)
