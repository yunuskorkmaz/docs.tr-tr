---
title: İki Diziyi Birleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: a2f2510cb334f4e22a7b0c6015a0a93b4dc11579
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142785"
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="509e7-102">İki Diziyi Birleştirme</span><span class="sxs-lookup"><span data-stu-id="509e7-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="509e7-103">Kullanım <xref:System.Linq.Queryable.Concat%2A> iki diziyi birleştirme için işleci.</span><span class="sxs-lookup"><span data-stu-id="509e7-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="509e7-104"><xref:System.Linq.Queryable.Concat%2A> İşleci siparişleri alıcı ve bağımsız değişken olduğu aynı sıralı multisets için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="509e7-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="509e7-105">Sonuçları üretti önce SQL sıralama son adımdır.</span><span class="sxs-lookup"><span data-stu-id="509e7-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="509e7-106">Bu nedenle, <xref:System.Linq.Queryable.Concat%2A> işleci kullanılarak gerçekleştirilen `UNION ALL` ve bağımsız değişkenlerinin sırası korumaz.</span><span class="sxs-lookup"><span data-stu-id="509e7-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="509e7-107">Sonuçlarda doğru sıralama emin olmak için açıkça sonuçlarını sıralama emin olun.</span><span class="sxs-lookup"><span data-stu-id="509e7-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="509e7-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="509e7-108">Example</span></span>  
 <span data-ttu-id="509e7-109">Bu örnekte <xref:System.Linq.Queryable.Concat%2A> tüm bir dizisini döndürmek için `Customer` ve `Employee` telefon ve Faks numaraları.</span><span class="sxs-lookup"><span data-stu-id="509e7-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="509e7-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="509e7-110">Example</span></span>  
 <span data-ttu-id="509e7-111">Bu örnekte <xref:System.Linq.Queryable.Concat%2A> tüm bir dizisini döndürmek için `Customer` ve `Employee` adlandırın ve telefon numarası eşlemeleri.</span><span class="sxs-lookup"><span data-stu-id="509e7-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="509e7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="509e7-112">See also</span></span>

- [<span data-ttu-id="509e7-113">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="509e7-113">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="509e7-114">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="509e7-114">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
