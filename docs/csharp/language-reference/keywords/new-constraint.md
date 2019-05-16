---
title: New kısıtlaması - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 32fcb13e1f217707d53300c532169b1a1759fa7e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633404"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="65ee4-102">New kısıtlaması (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="65ee4-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="65ee4-103">`new` Kısıtlaması belirtir bir genel sınıf bildiriminde herhangi bir tür bağımsız değişkeni genel bir parametresiz oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="65ee4-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="65ee4-104">New'kısıtlamasının kullanılabilmesi için türü soyut olamaz.</span><span class="sxs-lookup"><span data-stu-id="65ee4-104">To use the new constraint, the type cannot be abstract.</span></span>

## <a name="example"></a><span data-ttu-id="65ee4-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="65ee4-105">Example</span></span>

<span data-ttu-id="65ee4-106">Uygulama `new` öğesini aşağıdaki örnekte gösterildiği gibi genel bir sınıf türünün yeni örneğini oluşturduğunda, bir tür parametresi kısıtlaması:</span><span class="sxs-lookup"><span data-stu-id="65ee4-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a><span data-ttu-id="65ee4-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="65ee4-107">Example</span></span>

<span data-ttu-id="65ee4-108">Kullanırken `new()` kısıtlama diğer kısıtlamalarla en son belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="65ee4-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="65ee4-109">Daha fazla bilgi için [tür parametrelerindeki kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="65ee4-109">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="65ee4-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="65ee4-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="65ee4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65ee4-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="65ee4-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="65ee4-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="65ee4-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="65ee4-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="65ee4-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="65ee4-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="65ee4-115">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="65ee4-115">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="65ee4-116">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="65ee4-116">Generics</span></span>](../../programming-guide/generics/index.md)
