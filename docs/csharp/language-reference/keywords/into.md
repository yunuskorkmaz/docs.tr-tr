---
description: -C# başvurusu
title: -C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: 4712a6906195c5d8bc09c7b734dba0df4d2b08c8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134529"
---
# <a name="into-c-reference"></a><span data-ttu-id="49a74-103">into (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="49a74-103">into (C# Reference)</span></span>

<span data-ttu-id="49a74-104">`into`Bağlamsal anahtar sözcüğü bir [Grup](group-clause.md), [JOIN](join-clause.md) veya [Select](select-clause.md) yan tümcesinin sonuçlarını yeni bir tanımlayıcıya depolamak üzere geçici bir tanımlayıcı oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="49a74-104">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="49a74-105">Bu tanımlayıcı, ek sorgu komutları için bir Oluşturucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="49a74-105">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="49a74-106">`group`Or `select` yan tümcesinde kullanıldığında, yeni tanımlayıcının kullanımı bazen *devamlılık*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="49a74-106">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="49a74-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="49a74-107">Example</span></span>

<span data-ttu-id="49a74-108">Aşağıdaki örnek, `into` `fruitGroup` öğesinin çıkarılan bir türü olan geçici tanımlayıcıyı etkinleştirmek için anahtar sözcüğünün kullanımını gösterir `IGrouping` .</span><span class="sxs-lookup"><span data-stu-id="49a74-108">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="49a74-109">Tanımlayıcıyı kullanarak, <xref:System.Linq.Enumerable.Count%2A> her grupta yöntemi çağırabilir ve yalnızca iki veya daha fazla sözcük içeren grupları seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49a74-109">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="49a74-110">`into` `group` Yan tümcelerinde kullanılması yalnızca her grupta ek sorgu işlemleri gerçekleştirmek istediğinizde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="49a74-110">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="49a74-111">Daha fazla bilgi için bkz. [Group yan tümcesi](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="49a74-111">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="49a74-112">`into`Bir yan tümcedeki kullanımına bir örnek için `join` bkz. [JOIN yan tümcesi](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="49a74-112">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="49a74-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49a74-113">See also</span></span>

- [<span data-ttu-id="49a74-114">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="49a74-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="49a74-115">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="49a74-115">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="49a74-116">group tümcesi</span><span class="sxs-lookup"><span data-stu-id="49a74-116">group clause</span></span>](group-clause.md)
