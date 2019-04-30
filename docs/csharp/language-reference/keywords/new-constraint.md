---
title: New kısıtlaması - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: de0798319d91032143cb806d6d39338c4f51ac8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661171"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="91e3d-102">New kısıtlaması (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="91e3d-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="91e3d-103">`new` Kısıtlaması belirtir bir genel sınıf bildiriminde herhangi bir tür bağımsız değişkeni genel bir parametresiz oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91e3d-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="91e3d-104">New'kısıtlamasının kullanılabilmesi için türü soyut olamaz.</span><span class="sxs-lookup"><span data-stu-id="91e3d-104">To use the new constraint, the type cannot be abstract.</span></span>

## <a name="example"></a><span data-ttu-id="91e3d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="91e3d-105">Example</span></span>

<span data-ttu-id="91e3d-106">Uygulama `new` öğesini aşağıdaki örnekte gösterildiği gibi genel bir sınıf türünün yeni örneğini oluşturduğunda, bir tür parametresi kısıtlaması:</span><span class="sxs-lookup"><span data-stu-id="91e3d-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a><span data-ttu-id="91e3d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="91e3d-107">Example</span></span>

<span data-ttu-id="91e3d-108">Kullanırken `new()` kısıtlama diğer kısıtlamalarla en son belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="91e3d-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="91e3d-109">Daha fazla bilgi için [tür parametrelerindeki kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="91e3d-109">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="91e3d-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="91e3d-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="91e3d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91e3d-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="91e3d-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="91e3d-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="91e3d-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="91e3d-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="91e3d-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="91e3d-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="91e3d-115">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="91e3d-115">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="91e3d-116">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="91e3d-116">Generics</span></span>](../../programming-guide/generics/index.md)