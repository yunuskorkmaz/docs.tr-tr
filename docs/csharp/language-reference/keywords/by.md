---
title: bağlamsal anahtar kelimeye göre - C# Reference
ms.date: 07/20/2015
f1_keywords:
- by
- by_CSharpKeyword
helpviewer_keywords:
- by keyword [C#]
ms.assetid: efe6f0e3-be40-4df2-a144-c7db968ae052
ms.openlocfilehash: 4fa32a0dbfd8210ef8537aee849a55414b107a7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713728"
---
# <a name="by-c-reference"></a><span data-ttu-id="5b5c7-102">by (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5b5c7-102">by (C# Reference)</span></span>

<span data-ttu-id="5b5c7-103">İçeriksel `by` anahtar kelime, iade `group` edilen öğelerin nasıl gruplandırılmak gerektiğini belirtmek için sorgu ifadesindeki yan tümcede kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b5c7-103">The `by` contextual keyword is used in the `group` clause in a query expression to specify how the returned items should be grouped.</span></span> <span data-ttu-id="5b5c7-104">Daha fazla bilgi için [grup yan tümcesi'ne](./group-clause.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5b5c7-104">For more information, see [group clause](./group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="5b5c7-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b5c7-105">Example</span></span>

<span data-ttu-id="5b5c7-106">Aşağıdaki örnek, öğrencilerin her `by` öğrencinin soyadının `group` ilk harfine göre gruplandırılmak gerektiğini belirtmek için bir yan tümcedeki bağlamsal anahtar kelimenin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b5c7-106">The following example shows the use of the `by` contextual keyword in a `group` clause to specify that the students should be grouped according to the first letter of the last name of each student.</span></span>

[!code-csharp[csrefKeywordsContextual#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#10)]

## <a name="see-also"></a><span data-ttu-id="5b5c7-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b5c7-107">See also</span></span>

- [<span data-ttu-id="5b5c7-108">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="5b5c7-108">LINQ in C#</span></span>](../../linq/index.md)
