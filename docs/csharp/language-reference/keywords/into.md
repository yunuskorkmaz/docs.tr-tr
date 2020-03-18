---
title: into - C# Referans
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: f0f5ff1e56a65e83385f814df2fadd957f53561e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713621"
---
# <a name="into-c-reference"></a><span data-ttu-id="d8f74-102">into (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d8f74-102">into (C# Reference)</span></span>

<span data-ttu-id="d8f74-103">Bağlamsal anahtar kelime, bir [grubun](group-clause.md)sonuçlarını depolamak, yeni bir tanımlayıcıya yan tümceyi birleştirmek veya [seçmek](select-clause.md) için geçici bir tanımlayıcı oluşturmak için kullanılabilir. [join](join-clause.md) `into`</span><span class="sxs-lookup"><span data-stu-id="d8f74-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="d8f74-104">Bu tanımlayıcı, ek sorgu komutları için bir jeneratör olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8f74-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="d8f74-105">Bir `group` veya `select` yan tümcede kullanıldığında, yeni tanımlayıcının kullanımı bazen *devamı*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d8f74-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="d8f74-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8f74-106">Example</span></span>

<span data-ttu-id="d8f74-107">Aşağıdaki `into` örnekte, çıkarılan bir tür `fruitGroup` `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="d8f74-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="d8f74-108">Tanımlayıcıyı kullanarak, her gruptaki <xref:System.Linq.Enumerable.Count%2A> yöntemi çağırabilir ve yalnızca iki veya daha fazla sözcük içeren grupları seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8f74-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="d8f74-109">Bir `group` yan `into` tümcenin kullanımı yalnızca her grupta ek sorgu işlemleri gerçekleştirmek istediğinizde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d8f74-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="d8f74-110">Daha fazla bilgi için [grup yan tümcesi'ne](group-clause.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d8f74-110">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="d8f74-111">Bir yan tümcenin `into` kullanımına `join` ilişkin bir örnek için, [birleştirme yan tümcesi'ne](join-clause.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d8f74-111">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8f74-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8f74-112">See also</span></span>

- [<span data-ttu-id="d8f74-113">Sorgu Anahtar Kelimeleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d8f74-113">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="d8f74-114">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="d8f74-114">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="d8f74-115">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d8f74-115">group clause</span></span>](group-clause.md)
