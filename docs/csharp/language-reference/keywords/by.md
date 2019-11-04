---
title: Bağlamsal anahtar sözcüğe göre C# -başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- by
- by_CSharpKeyword
helpviewer_keywords:
- by keyword [C#]
ms.assetid: efe6f0e3-be40-4df2-a144-c7db968ae052
ms.openlocfilehash: 9f888f170f749eb5aac5cd39cd7c733920581542
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422879"
---
# <a name="by-c-reference"></a><span data-ttu-id="3aff1-102">by (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3aff1-102">by (C# Reference)</span></span>

<span data-ttu-id="3aff1-103">`by` bağlamsal anahtar sözcüğü, döndürülen öğelerin nasıl gruplanacağını belirtmek için bir sorgu ifadesindeki `group` yan tümcesinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3aff1-103">The `by` contextual keyword is used in the `group` clause in a query expression to specify how the returned items should be grouped.</span></span> <span data-ttu-id="3aff1-104">Daha fazla bilgi için bkz. [Group yan tümcesi](./group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="3aff1-104">For more information, see [group clause](./group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="3aff1-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3aff1-105">Example</span></span>

<span data-ttu-id="3aff1-106">Aşağıdaki örnek, öğrencilerin her öğrencinin son adının ilk harfine göre gruplanacağını belirtmek için bir `group` yan tümcesinde `by` bağlamsal anahtar sözcüğünün kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3aff1-106">The following example shows the use of the `by` contextual keyword in a `group` clause to specify that the students should be grouped according to the first letter of the last name of each student.</span></span>

[!code-csharp[csrefKeywordsContextual#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#10)]

## <a name="see-also"></a><span data-ttu-id="3aff1-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3aff1-107">See also</span></span>

- [<span data-ttu-id="3aff1-108">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="3aff1-108">LINQ in C#</span></span>](../../linq/index.md)
