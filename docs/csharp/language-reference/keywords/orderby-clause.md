---
title: maddesi uyarınca sipariş - C# Referans
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: cd76b2c33fe1a1a986bc05e3c3ed5f22809686ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173581"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="ca329-102">orderby tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ca329-102">orderby clause (C# Reference)</span></span>

<span data-ttu-id="ca329-103">Sorgu ifadesinde, `orderby` yan tümce, döndürülen sıranın veya alt dizinin (grup) artan veya azalan sırada sıralanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="ca329-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="ca329-104">Bir veya daha fazla ikincil sıralama işlemi gerçekleştirmek için birden çok anahtar belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="ca329-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="ca329-105">Sıralama öğesi türü için varsayılan karşılayıcı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ca329-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="ca329-106">Varsayılan sıralama sırası yükseliyor.</span><span class="sxs-lookup"><span data-stu-id="ca329-106">The default sort order is ascending.</span></span> <span data-ttu-id="ca329-107">Özel bir karşılayıcı da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca329-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="ca329-108">Ancak, yalnızca yöntem tabanlı sözdizimi kullanılarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ca329-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="ca329-109">Daha fazla bilgi için [bkz.](../../programming-guide/concepts/linq/sorting-data.md)</span><span class="sxs-lookup"><span data-stu-id="ca329-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="ca329-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca329-110">Example</span></span>

<span data-ttu-id="ca329-111">Aşağıdaki örnekte, ilk sorgu sözcükleri A'dan başlayarak alfabetik sıraya göre sıralar, ikinci sorgu ise aynı sözcükleri azalan sırada sıralar.</span><span class="sxs-lookup"><span data-stu-id="ca329-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="ca329-112">(Anahtar `ascending` kelime varsayılan sıralama değeridir ve atlanabilir.)</span><span class="sxs-lookup"><span data-stu-id="ca329-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="ca329-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca329-113">Example</span></span>

<span data-ttu-id="ca329-114">Aşağıdaki örnekte, öğrencilerin soyadlarına bir birincil sıralama ve daha sonra ilk adlarında ikincil sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ca329-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="ca329-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca329-115">Remarks</span></span>

<span data-ttu-id="ca329-116">Derleme zamanında, `orderby` yan tümce <xref:System.Linq.Enumerable.OrderBy%2A> yönteme bir çağrıya çevrilir.</span><span class="sxs-lookup"><span data-stu-id="ca329-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="ca329-117">`orderby` Yan tümcedeki birden <xref:System.Linq.Enumerable.ThenBy%2A> çok anahtar yöntem çağrılarına çevirir.</span><span class="sxs-lookup"><span data-stu-id="ca329-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca329-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca329-118">See also</span></span>

- [<span data-ttu-id="ca329-119">C# Referans</span><span class="sxs-lookup"><span data-stu-id="ca329-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ca329-120">Sorgu Anahtar Kelimeleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="ca329-120">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="ca329-121">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="ca329-121">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="ca329-122">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="ca329-122">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="ca329-123">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="ca329-123">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
