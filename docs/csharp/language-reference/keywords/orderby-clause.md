---
title: OrderBy yan tümcesi C# -başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 09a745fe3da3a5acb71972b9cf56391774c7016a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422649"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="04570-102">orderby tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="04570-102">orderby clause (C# Reference)</span></span>

<span data-ttu-id="04570-103">Sorgu ifadesinde `orderby` yan tümcesi, döndürülen sıranın veya alt dizinin (Grup) artan veya azalan sırada sıralanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="04570-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="04570-104">Bir veya daha fazla ikincil sıralama işlemi gerçekleştirmek için birden çok anahtar belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="04570-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="04570-105">Sıralama, öğe türü için varsayılan karşılaştırıcı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="04570-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="04570-106">Varsayılan sıralama düzeni artan.</span><span class="sxs-lookup"><span data-stu-id="04570-106">The default sort order is ascending.</span></span> <span data-ttu-id="04570-107">Ayrıca, özel bir karşılaştırıcı da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04570-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="04570-108">Ancak, yalnızca Yöntem tabanlı sözdizimi kullanılarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="04570-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="04570-109">Daha fazla bilgi için bkz. [verileri sıralama](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="04570-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="04570-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="04570-110">Example</span></span>

<span data-ttu-id="04570-111">Aşağıdaki örnekte, ilk sorgu kelimeleri bir ' dan başlayarak alfabetik sırada sıralar ve ikinci sorgu aynı sözcükleri azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="04570-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="04570-112">(`ascending` anahtar sözcüğü varsayılan sıralama değeridir ve atlanabilir.)</span><span class="sxs-lookup"><span data-stu-id="04570-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="04570-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="04570-113">Example</span></span>

<span data-ttu-id="04570-114">Aşağıdaki örnek, öğrencilerin soyadı üzerinde birincil bir sıralama ve ardından ilk adlarında ikinci bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="04570-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="04570-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04570-115">Remarks</span></span>

<span data-ttu-id="04570-116">Derleme zamanında, `orderby` yan tümcesi <xref:System.Linq.Enumerable.OrderBy%2A> yöntemine yapılan çağrıya çevrilir.</span><span class="sxs-lookup"><span data-stu-id="04570-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="04570-117">`orderby` yan tümcesindeki birden çok anahtar <xref:System.Linq.Enumerable.ThenBy%2A> yöntemi çağrılarına çeviri yapar.</span><span class="sxs-lookup"><span data-stu-id="04570-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="04570-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04570-118">See also</span></span>

- [<span data-ttu-id="04570-119">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="04570-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="04570-120">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="04570-120">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="04570-121">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="04570-121">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="04570-122">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="04570-122">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="04570-123">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="04570-123">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
