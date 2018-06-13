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
ms.openlocfilehash: 1fd0036e8bd3c838fe92ca27635cd7638d59ef1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268063"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="c5817-102">orderby tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c5817-102">orderby clause (C# Reference)</span></span>
<span data-ttu-id="c5817-103">Bir sorgu ifadesinde `orderby` yan tümcesi döndürülen dizi veya değişkene (artan veya azalan düzende sıralanmış grup) neden olur.</span><span class="sxs-lookup"><span data-stu-id="c5817-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="c5817-104">Birden çok anahtar, bir veya daha fazla ikincil sıralama işlemi gerçekleştirmek için belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5817-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="c5817-105">Sıralama öğesi türü için varsayılan karşılaştırıcı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c5817-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="c5817-106">Varsayılan sıralama düzeni artan.</span><span class="sxs-lookup"><span data-stu-id="c5817-106">The default sort order is ascending.</span></span> <span data-ttu-id="c5817-107">Özel bir karşılaştırıcı de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5817-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="c5817-108">Ancak, yalnızca yöntemi tabanlı sözdizimini kullanarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5817-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="c5817-109">Daha fazla bilgi için bkz: [veri sıralama](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="c5817-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5817-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5817-110">Example</span></span>  
 <span data-ttu-id="c5817-111">Aşağıdaki örnekte, ilk sorgu sözcükleri A'dan başlangıç alfabetik sırada sıralar ve ikinci sorguyu aynı sözcükler azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="c5817-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="c5817-112">( `ascending` Anahtar sözcüğü varsayılan sıralama değerdir ve atlanabilir.)</span><span class="sxs-lookup"><span data-stu-id="c5817-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="c5817-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5817-113">Example</span></span>  
 <span data-ttu-id="c5817-114">Aşağıdaki örnek ilk adlarını Öğrenciler son adları birincil sıralama ve ikincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c5817-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="c5817-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5817-115">Remarks</span></span>  
 <span data-ttu-id="c5817-116">Derleme zamanında `orderby` yan tümcesi için bir çağrı çevrilir <xref:System.Linq.Enumerable.OrderBy%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c5817-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="c5817-117">Birden çok anahtarlar `orderby` yan tümcesi çevirmek için <xref:System.Linq.Enumerable.ThenBy%2A> yöntem çağrıları.</span><span class="sxs-lookup"><span data-stu-id="c5817-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5817-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5817-118">See Also</span></span>  
 [<span data-ttu-id="c5817-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c5817-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c5817-120">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c5817-120">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="c5817-121">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="c5817-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="c5817-122">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c5817-122">group clause</span></span>](../../../csharp/language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="c5817-123">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="c5817-123">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
