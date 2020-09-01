---
description: by bağlamsal anahtar sözcüğe-C# başvurusu
title: by bağlamsal anahtar sözcüğe-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- by
- by_CSharpKeyword
helpviewer_keywords:
- by keyword [C#]
ms.assetid: efe6f0e3-be40-4df2-a144-c7db968ae052
ms.openlocfilehash: 2bc62f6f7f9e8a6d434ea254d5b04e563c41bc26
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134698"
---
# <a name="by-c-reference"></a><span data-ttu-id="c3b3b-103">by (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c3b3b-103">by (C# Reference)</span></span>

<span data-ttu-id="c3b3b-104">`by`Bağlamsal anahtar sözcüğü, `group` döndürülen öğelerin nasıl gruplanacağını belirtmek için bir sorgu ifadesinin yan tümcesinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c3b3b-104">The `by` contextual keyword is used in the `group` clause in a query expression to specify how the returned items should be grouped.</span></span> <span data-ttu-id="c3b3b-105">Daha fazla bilgi için bkz. [Group yan tümcesi](./group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c3b3b-105">For more information, see [group clause](./group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="c3b3b-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3b3b-106">Example</span></span>

<span data-ttu-id="c3b3b-107">Aşağıdaki örnek, `by` `group` öğrencilerin her öğrencinin son adının ilk harfine göre gruplanıp gruplandırılmadığını belirtmek için bir yan tümce içinde bağlamsal anahtar sözcüğünün kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3b3b-107">The following example shows the use of the `by` contextual keyword in a `group` clause to specify that the students should be grouped according to the first letter of the last name of each student.</span></span>

[!code-csharp[csrefKeywordsContextual#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#10)]

## <a name="see-also"></a><span data-ttu-id="c3b3b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3b3b-108">See also</span></span>

- [<span data-ttu-id="c3b3b-109">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="c3b3b-109">LINQ in C#</span></span>](../../linq/index.md)
