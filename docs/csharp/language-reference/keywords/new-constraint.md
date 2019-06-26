---
title: New kısıtlaması - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 7c788be52010cdfadbd3c03f9e570815d25bdbef
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401488"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="36372-102">New kısıtlaması (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="36372-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="36372-103">`new` Kısıtlaması belirtir bir genel sınıf bildiriminde tür bağımsız değişkeni genel bir parametresiz oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="36372-103">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="36372-104">Kullanılacak `new` kısıtlaması, türü olamaz abstract.</span><span class="sxs-lookup"><span data-stu-id="36372-104">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="36372-105">Uygulama `new` öğesini aşağıdaki örnekte gösterildiği gibi genel bir sınıf türünün yeni örneğini oluşturduğunda, bir tür parametresi kısıtlaması:</span><span class="sxs-lookup"><span data-stu-id="36372-105">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="36372-106">Kullanırken `new()` kısıtlama diğer kısıtlamalarla en son belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="36372-106">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="36372-107">Daha fazla bilgi için [tür parametrelerindeki kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="36372-107">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="36372-108">De kullanabilirsiniz `new` anahtar [bir türün bir örneğini oluşturma](../operators/new-operator.md) veya farklı bir [üye bildirim değiştirici](new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="36372-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="36372-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="36372-109">C# language specification</span></span>

<span data-ttu-id="36372-110">Daha fazla bilgi için [tür parametresi kısıtlamaları](~/_csharplang/spec/classes.md#type-parameter-constraints) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="36372-110">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="36372-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36372-111">See also</span></span>

- [<span data-ttu-id="36372-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="36372-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="36372-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="36372-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="36372-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="36372-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="36372-115">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="36372-115">Generics</span></span>](../../programming-guide/generics/index.md)
