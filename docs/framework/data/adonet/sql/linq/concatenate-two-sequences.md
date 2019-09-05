---
title: İki Diziyi Birleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: b802abae9fc2c1731a623209862f61ed5ee51f9c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247882"
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="942f9-102">İki Diziyi Birleştirme</span><span class="sxs-lookup"><span data-stu-id="942f9-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="942f9-103">İki diziyi birleştirmek için işlecinikullanın.<xref:System.Linq.Queryable.Concat%2A></span><span class="sxs-lookup"><span data-stu-id="942f9-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="942f9-104"><xref:System.Linq.Queryable.Concat%2A> İşleci, alıcı ve bağımsız değişken siparişlerinin aynı olduğu sıralı çoklu kümeler için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="942f9-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="942f9-105">SQL 'de sıralama sonuçları üretilmekte olan son adımdır.</span><span class="sxs-lookup"><span data-stu-id="942f9-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="942f9-106">Bu nedenle, <xref:System.Linq.Queryable.Concat%2A> işleci kullanılarak `UNION ALL` uygulanır ve bağımsız değişkenlerinin sırasını korumaz.</span><span class="sxs-lookup"><span data-stu-id="942f9-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="942f9-107">Sonuçların sonuçlarda doğru olduğundan emin olmak için sonuçları açıkça sıralediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="942f9-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="942f9-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="942f9-108">Example</span></span>  
 <span data-ttu-id="942f9-109">Bu örnek, <xref:System.Linq.Queryable.Concat%2A> tüm `Customer` ve `Employee` telefon ve faks numaralarının bir dizisini döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="942f9-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="942f9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="942f9-110">Example</span></span>  
 <span data-ttu-id="942f9-111">Bu örnek, <xref:System.Linq.Queryable.Concat%2A> tüm `Customer` ve `Employee` ad ve telefon numarası eşlemelerinin bir dizisini döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="942f9-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="942f9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="942f9-112">See also</span></span>

- [<span data-ttu-id="942f9-113">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="942f9-113">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="942f9-114">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="942f9-114">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
