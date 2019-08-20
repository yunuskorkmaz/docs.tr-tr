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
ms.openlocfilehash: 23daf2aaf5d9456c76c5b2ac889243b1ed31b077
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602217"
---
# <a name="by-c-reference"></a><span data-ttu-id="c75b0-102">by (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c75b0-102">by (C# Reference)</span></span>

<span data-ttu-id="c75b0-103">Bağlamsal anahtar sözcüğü, döndürülen öğelerin nasıl `group` gruplanacağını belirtmek için bir sorgu ifadesinin yan tümcesinde kullanılır. `by`</span><span class="sxs-lookup"><span data-stu-id="c75b0-103">The `by` contextual keyword is used in the `group` clause in a query expression to specify how the returned items should be grouped.</span></span> <span data-ttu-id="c75b0-104">Daha fazla bilgi için bkz. [Group yan tümcesi](./group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c75b0-104">For more information, see [group clause](./group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="c75b0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c75b0-105">Example</span></span>

<span data-ttu-id="c75b0-106">Aşağıdaki örnek, öğrencilerin her öğrencinin son adının `by` ilk harfine göre gruplanıp gruplandırılmadığını belirtmek için bir `group` yan tümce içinde bağlamsal anahtar sözcüğünün kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c75b0-106">The following example shows the use of the `by` contextual keyword in a `group` clause to specify that the students should be grouped according to the first letter of the last name of each student.</span></span>

[!code-csharp[csrefKeywordsContextual#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#10)]

## <a name="see-also"></a><span data-ttu-id="c75b0-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c75b0-107">See also</span></span>

- [<span data-ttu-id="c75b0-108">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="c75b0-108">LINQ Query Expressions</span></span>](../../programming-guide/linq-query-expressions/index.md)
