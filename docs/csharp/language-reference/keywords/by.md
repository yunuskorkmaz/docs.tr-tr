---
title: bağlamsal anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- by
- by_CSharpKeyword
helpviewer_keywords:
- by keyword [C#]
ms.assetid: efe6f0e3-be40-4df2-a144-c7db968ae052
ms.openlocfilehash: e1748948ce6e036d0a3791940fd900f79f27d51f
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315140"
---
# <a name="by-c-reference"></a><span data-ttu-id="0315e-102">by (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0315e-102">by (C# Reference)</span></span>

<span data-ttu-id="0315e-103">`by` Bağlamsal anahtar sözcüğü kullanılır `group` döndürülen öğeleri nasıl gruplandırılmalıdır belirtmek için bir sorgu ifadesinde yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="0315e-103">The `by` contextual keyword is used in the `group` clause in a query expression to specify how the returned items should be grouped.</span></span> <span data-ttu-id="0315e-104">Daha fazla bilgi için bkz: [group yan tümcesi](../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0315e-104">For more information, see [group clause](../../../csharp/language-reference/keywords/group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="0315e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0315e-105">Example</span></span>

<span data-ttu-id="0315e-106">Aşağıdaki örnek kullanımı gösterilmiştir `by` bağlamsal anahtar sözcüğü bir `group` Öğrenciler her öğrencinin son adının ilk harfi göre gruplandırılmış olduğunu belirtmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="0315e-106">The following example shows the use of the `by` contextual keyword in a `group` clause to specify that the students should be grouped according to the first letter of the last name of each student.</span></span>

[!code-csharp[csrefKeywordsContextual#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#10)]

## <a name="see-also"></a><span data-ttu-id="0315e-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0315e-107">See also</span></span>

[<span data-ttu-id="0315e-108">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="0315e-108">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
