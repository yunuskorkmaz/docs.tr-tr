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
ms.openlocfilehash: ccb1463db51510d275b7053955a0257bd4fe621e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422705"
---
# <a name="into-c-reference"></a><span data-ttu-id="41a07-102">into (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="41a07-102">into (C# Reference)</span></span>

<span data-ttu-id="41a07-103">`into` bağlamsal anahtar sözcüğü, bir [Grup](group-clause.md), [JOIN](join-clause.md) veya [Select](select-clause.md) yan tümcesinin sonuçlarını yeni bir tanımlayıcıya depolamak üzere geçici bir tanımlayıcı oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="41a07-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="41a07-104">Bu tanımlayıcı, ek sorgu komutları için bir Oluşturucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="41a07-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="41a07-105">Bir `group` veya `select` yan tümcesinde kullanıldığında, yeni tanımlayıcının kullanımı bazen *devamlılık*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="41a07-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="41a07-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="41a07-106">Example</span></span>

<span data-ttu-id="41a07-107">Aşağıdaki örnek, `fruitGroup` bir `IGrouping`türü olan geçici bir tanımlayıcıyı etkinleştirmek için `into` anahtar sözcüğünün kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="41a07-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="41a07-108">Tanımlayıcıyı kullanarak, her grupta <xref:System.Linq.Enumerable.Count%2A> yöntemi çağırabilir ve yalnızca iki veya daha fazla sözcük içeren grupları seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41a07-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="41a07-109">`group` yan tümcesinde `into` kullanımı yalnızca her grupta ek sorgu işlemleri gerçekleştirmek istediğinizde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="41a07-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="41a07-110">Daha fazla bilgi için bkz. [Group yan tümcesi](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="41a07-110">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="41a07-111">Bir `join` yan tümcesinde `into` kullanımı örneği için bkz. [JOIN yan tümcesi](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="41a07-111">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="41a07-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41a07-112">See also</span></span>

- [<span data-ttu-id="41a07-113">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="41a07-113">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="41a07-114">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="41a07-114">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="41a07-115">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="41a07-115">group clause</span></span>](group-clause.md)
