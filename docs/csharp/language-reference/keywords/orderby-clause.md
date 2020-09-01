---
description: OrderBy tümcesi-C# başvurusu
title: OrderBy tümcesi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 2f64b45ff252c7cc02e56c465da21ccc5e861aec
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142355"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="b9588-103">orderby tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b9588-103">orderby clause (C# Reference)</span></span>

<span data-ttu-id="b9588-104">Bir sorgu ifadesinde `orderby` yan tümce döndürülen sıranın veya alt dizinin (Grup) artan veya azalan sırada sıralanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9588-104">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="b9588-105">Bir veya daha fazla ikincil sıralama işlemi gerçekleştirmek için birden çok anahtar belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b9588-105">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="b9588-106">Sıralama, öğe türü için varsayılan karşılaştırıcı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b9588-106">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="b9588-107">Varsayılan sıralama düzeni artan.</span><span class="sxs-lookup"><span data-stu-id="b9588-107">The default sort order is ascending.</span></span> <span data-ttu-id="b9588-108">Ayrıca, özel bir karşılaştırıcı da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9588-108">You can also specify a custom comparer.</span></span> <span data-ttu-id="b9588-109">Ancak, yalnızca Yöntem tabanlı sözdizimi kullanılarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b9588-109">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="b9588-110">Daha fazla bilgi için bkz. [verileri sıralama](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="b9588-110">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="b9588-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9588-111">Example</span></span>

<span data-ttu-id="b9588-112">Aşağıdaki örnekte, ilk sorgu kelimeleri bir ' dan başlayarak alfabetik sırada sıralar ve ikinci sorgu aynı sözcükleri azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="b9588-112">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="b9588-113">( `ascending` Anahtar sözcüğü varsayılan sıralama değeridir ve atlanabilir.)</span><span class="sxs-lookup"><span data-stu-id="b9588-113">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="b9588-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9588-114">Example</span></span>

<span data-ttu-id="b9588-115">Aşağıdaki örnek, öğrencilerin soyadı üzerinde birincil bir sıralama ve ardından ilk adlarında ikinci bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="b9588-115">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="b9588-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9588-116">Remarks</span></span>

<span data-ttu-id="b9588-117">Derleme zamanında `orderby` yan tümce yöntemine bir çağrıya çevrilir <xref:System.Linq.Enumerable.OrderBy%2A> .</span><span class="sxs-lookup"><span data-stu-id="b9588-117">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="b9588-118">Yan tümcesindeki birden çok anahtar `orderby` <xref:System.Linq.Enumerable.ThenBy%2A> metot çağrılarına çeviri yapar.</span><span class="sxs-lookup"><span data-stu-id="b9588-118">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9588-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9588-119">See also</span></span>

- [<span data-ttu-id="b9588-120">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b9588-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b9588-121">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="b9588-121">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="b9588-122">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="b9588-122">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="b9588-123">group tümcesi</span><span class="sxs-lookup"><span data-stu-id="b9588-123">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="b9588-124">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="b9588-124">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
