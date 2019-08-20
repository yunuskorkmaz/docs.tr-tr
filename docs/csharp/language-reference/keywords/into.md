---
title: C# başvuruya göre
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: dc1e2ee004c21bb3d05155eec3e42ea80bf641a1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608644"
---
# <a name="into-c-reference"></a><span data-ttu-id="f1902-102">into (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f1902-102">into (C# Reference)</span></span>

<span data-ttu-id="f1902-103">Bağlamsal anahtar sözcüğü bir [Grup](group-clause.md), [JOIN](join-clause.md) veya Select yan tümcesinin sonuçlarını yeni bir tanımlayıcıya depolamak üzere geçici bir tanımlayıcı oluşturmak için kullanılabilir. [](select-clause.md) `into`</span><span class="sxs-lookup"><span data-stu-id="f1902-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="f1902-104">Bu tanımlayıcı, ek sorgu komutları için bir Oluşturucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1902-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="f1902-105">`group` Or`select` yan tümcesinde kullanıldığında, yeni tanımlayıcının kullanımı bazen *devamlılık*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f1902-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="f1902-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1902-106">Example</span></span>

<span data-ttu-id="f1902-107">Aşağıdaki örnek, öğesinin `into` `IGrouping`çıkarılan bir türü olan geçici tanımlayıcıyı `fruitGroup` etkinleştirmek için anahtar sözcüğünün kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1902-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="f1902-108">Tanımlayıcıyı kullanarak, her grupta <xref:System.Linq.Enumerable.Count%2A> yöntemi çağırabilir ve yalnızca iki veya daha fazla sözcük içeren grupları seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1902-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="f1902-109">`into` Yan tümcelerinde kullanılması yalnızca her grupta ek sorgu işlemleri gerçekleştirmek istediğinizde gereklidir. `group`</span><span class="sxs-lookup"><span data-stu-id="f1902-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="f1902-110">Daha fazla bilgi için bkz. [Group yan tümcesi](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f1902-110">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="f1902-111">`into` Bir`join` yan tümcedeki kullanımına bir örnek için bkz. [JOIN yan tümcesi](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f1902-111">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f1902-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1902-112">See also</span></span>

- [<span data-ttu-id="f1902-113">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f1902-113">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="f1902-114">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="f1902-114">LINQ Query Expressions</span></span>](../../programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="f1902-115">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="f1902-115">group clause</span></span>](group-clause.md)
