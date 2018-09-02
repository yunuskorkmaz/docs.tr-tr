---
title: orderby tümcesi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: de649a7e1608e6a653f3280bfd5c4e52a3b661be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391203"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="08e9d-102">orderby tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="08e9d-102">orderby clause (C# Reference)</span></span>

<span data-ttu-id="08e9d-103">Bir sorgu ifadesinde `orderby` yan tümcesi döndürülen dizi veya alt diziyi artan veya azalan düzende sıralanmasını (grubu) neden olur.</span><span class="sxs-lookup"><span data-stu-id="08e9d-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="08e9d-104">Birden çok anahtar, bir veya daha fazla ikincil sıralama işlemlerini gerçekleştirmek için belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="08e9d-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="08e9d-105">Sıralama, öğe türü için varsayılan karşılaştırıcı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="08e9d-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="08e9d-106">Varsayılan sıralama artan düzendedir.</span><span class="sxs-lookup"><span data-stu-id="08e9d-106">The default sort order is ascending.</span></span> <span data-ttu-id="08e9d-107">Özel bir karşılaştırıcı de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08e9d-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="08e9d-108">Ancak, yalnızca yöntem tabanlı sözdizimi kullanılarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="08e9d-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="08e9d-109">Daha fazla bilgi için [veri sıralama](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="08e9d-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="08e9d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="08e9d-110">Example</span></span>

<span data-ttu-id="08e9d-111">Aşağıdaki örnekte, A'dan başlayarak alfabetik sırada sözcükleri ilk sorgu sıralar ve ikinci sorgu aynı sözcükler azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="08e9d-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="08e9d-112">( `ascending` Anahtar sözcüğü atlanabilir ve varsayılan sıralama değerdir.)</span><span class="sxs-lookup"><span data-stu-id="08e9d-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="08e9d-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="08e9d-113">Example</span></span>

<span data-ttu-id="08e9d-114">Aşağıdaki örnek, ilk adlarına öğrencilerinin adların birincil bir sıralama ve ikincil sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="08e9d-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="08e9d-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08e9d-115">Remarks</span></span>

<span data-ttu-id="08e9d-116">Derleme zamanında `orderby` yan tümcesi bir çağrısına çevrilir <xref:System.Linq.Enumerable.OrderBy%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="08e9d-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="08e9d-117">Birden çok anahtarı `orderby` yan tümcesi çevirmek için <xref:System.Linq.Enumerable.ThenBy%2A> yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="08e9d-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="08e9d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08e9d-118">See also</span></span>

- [<span data-ttu-id="08e9d-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="08e9d-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="08e9d-120">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="08e9d-120">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="08e9d-121">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="08e9d-121">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="08e9d-122">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="08e9d-122">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="08e9d-123">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="08e9d-123">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)