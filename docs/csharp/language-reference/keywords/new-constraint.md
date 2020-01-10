---
title: Yeni kısıtlama- C# başvuru
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713349"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="906a7-102">Yeni kısıtlama (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="906a7-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="906a7-103">`new` kısıtlaması, genel sınıf bildirimindeki bir tür bağımsız değişkeninin Ortak parametresiz bir oluşturucuya sahip olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="906a7-103">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="906a7-104">`new` kısıtlamasını kullanmak için tür soyut olamaz.</span><span class="sxs-lookup"><span data-stu-id="906a7-104">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="906a7-105">Aşağıdaki örnekte gösterildiği gibi, genel bir sınıf türün yeni örneklerini oluşturduğunda, `new` kısıtlamasını bir tür parametresine uygulayın:</span><span class="sxs-lookup"><span data-stu-id="906a7-105">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="906a7-106">`new()` kısıtlamasını diğer kısıtlamalarla birlikte kullandığınızda, en son belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="906a7-106">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="906a7-107">Daha fazla bilgi için bkz. [tür parametrelerindeki kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="906a7-107">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="906a7-108">Ayrıca, [bir türün örneğini](../operators/new-operator.md) veya bir [üye bildirimi değiştiricisini](new-modifier.md)oluşturmak için `new` anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="906a7-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="906a7-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="906a7-109">C# language specification</span></span>

<span data-ttu-id="906a7-110">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [tür parametresi kısıtlamaları](~/_csharplang/spec/classes.md#type-parameter-constraints) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="906a7-110">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="906a7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="906a7-111">See also</span></span>

- [<span data-ttu-id="906a7-112">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="906a7-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="906a7-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="906a7-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="906a7-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="906a7-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="906a7-115">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="906a7-115">Generics</span></span>](../../programming-guide/generics/index.md)
