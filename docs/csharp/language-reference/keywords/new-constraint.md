---
title: yeni kısıtlama - C# Referans
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713349"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="30212-102">yeni kısıtlama (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="30212-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="30212-103">Kısıtlama, `new` genel bir sınıf bildirimindeki bir tür bağımsız değişkeninin ortak parametresiz bir oluşturucuya sahip olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="30212-103">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="30212-104">Kısıtlamayı `new` kullanmak için, tür soyut olamaz.</span><span class="sxs-lookup"><span data-stu-id="30212-104">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="30212-105">Genel `new` bir sınıf aşağıdaki örnekte gösterildiği gibi, tür yeni örnekler oluşturduğunda bir tür parametresine kısıtlama uygulayın:</span><span class="sxs-lookup"><span data-stu-id="30212-105">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="30212-106">Kısıtlamayı `new()` diğer kısıtlamalarla kullandığınızda, en son belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="30212-106">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="30212-107">Daha fazla bilgi [için, Tür Parametreleri üzerindeki Kısıtlamalar'a](../../programming-guide/generics/constraints-on-type-parameters.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="30212-107">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="30212-108">Anahtar kelimeyi, `new` bir [tür örneği oluşturmak](../operators/new-operator.md) veya [üye bildirimi değiştiricisi](new-modifier.md)olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30212-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="30212-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="30212-109">C# language specification</span></span>

<span data-ttu-id="30212-110">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Tür parametre kısıtlamaları](~/_csharplang/spec/classes.md#type-parameter-constraints) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="30212-110">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="30212-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30212-111">See also</span></span>

- [<span data-ttu-id="30212-112">C# Referans</span><span class="sxs-lookup"><span data-stu-id="30212-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="30212-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="30212-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="30212-114">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="30212-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="30212-115">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="30212-115">Generics</span></span>](../../programming-guide/generics/index.md)
