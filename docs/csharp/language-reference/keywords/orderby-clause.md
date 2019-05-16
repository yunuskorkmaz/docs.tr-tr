---
title: OrderBy yan tümcesinin - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: b62634c0f61e17c046cd474670fddf437287ab7a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634103"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="e8801-102">orderby tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e8801-102">orderby clause (C# Reference)</span></span>

<span data-ttu-id="e8801-103">Bir sorgu ifadesinde `orderby` yan tümcesi döndürülen dizi veya alt diziyi artan veya azalan düzende sıralanmasını (grubu) neden olur.</span><span class="sxs-lookup"><span data-stu-id="e8801-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="e8801-104">Birden çok anahtar, bir veya daha fazla ikincil sıralama işlemlerini gerçekleştirmek için belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e8801-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="e8801-105">Sıralama, öğe türü için varsayılan karşılaştırıcı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e8801-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="e8801-106">Varsayılan sıralama artan düzendedir.</span><span class="sxs-lookup"><span data-stu-id="e8801-106">The default sort order is ascending.</span></span> <span data-ttu-id="e8801-107">Özel bir karşılaştırıcı de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8801-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="e8801-108">Ancak, yalnızca yöntem tabanlı sözdizimi kullanılarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8801-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="e8801-109">Daha fazla bilgi için [veri sıralama](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="e8801-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="e8801-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8801-110">Example</span></span>

<span data-ttu-id="e8801-111">Aşağıdaki örnekte, A'dan başlayarak alfabetik sırada sözcükleri ilk sorgu sıralar ve ikinci sorgu aynı sözcükler azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="e8801-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="e8801-112">( `ascending` Anahtar sözcüğü atlanabilir ve varsayılan sıralama değerdir.)</span><span class="sxs-lookup"><span data-stu-id="e8801-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="e8801-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8801-113">Example</span></span>

<span data-ttu-id="e8801-114">Aşağıdaki örnek, ilk adlarına öğrencilerinin adların birincil bir sıralama ve ikincil sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e8801-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="e8801-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8801-115">Remarks</span></span>

<span data-ttu-id="e8801-116">Derleme zamanında `orderby` yan tümcesi bir çağrısına çevrilir <xref:System.Linq.Enumerable.OrderBy%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e8801-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="e8801-117">Birden çok anahtarı `orderby` yan tümcesi çevirmek için <xref:System.Linq.Enumerable.ThenBy%2A> yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="e8801-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8801-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8801-118">See also</span></span>

- [<span data-ttu-id="e8801-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e8801-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e8801-120">Query Keywords (LINQ)</span><span class="sxs-lookup"><span data-stu-id="e8801-120">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="e8801-121">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="e8801-121">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="e8801-122">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e8801-122">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="e8801-123">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="e8801-123">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)
