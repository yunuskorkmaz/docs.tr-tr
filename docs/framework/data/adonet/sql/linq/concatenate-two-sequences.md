---
description: 'Daha fazla bilgi edinin: Iki diziyi birleştirme'
title: İki Diziyi Birleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: 5e48f3e2900bf53d042eb9c2aad6535bad9ec7e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773179"
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="bd805-103">İki Diziyi Birleştirme</span><span class="sxs-lookup"><span data-stu-id="bd805-103">Concatenate Two Sequences</span></span>

<span data-ttu-id="bd805-104"><xref:System.Linq.Queryable.Concat%2A>İki diziyi birleştirmek için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd805-104">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="bd805-105"><xref:System.Linq.Queryable.Concat%2A>İşleci, alıcı ve bağımsız değişken siparişlerinin aynı olduğu sıralı çoklu kümeler için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="bd805-105">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="bd805-106">SQL 'de sıralama sonuçları üretilmekte olan son adımdır.</span><span class="sxs-lookup"><span data-stu-id="bd805-106">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="bd805-107">Bu nedenle, <xref:System.Linq.Queryable.Concat%2A> işleci kullanılarak uygulanır `UNION ALL` ve bağımsız değişkenlerinin sırasını korumaz.</span><span class="sxs-lookup"><span data-stu-id="bd805-107">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="bd805-108">Sonuçların sonuçlarda doğru olduğundan emin olmak için sonuçları açıkça sıralediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="bd805-108">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd805-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd805-109">Example</span></span>  

 <span data-ttu-id="bd805-110">Bu örnek, <xref:System.Linq.Queryable.Concat%2A> tüm `Customer` ve `Employee` telefon ve faks numaralarının bir dizisini döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd805-110">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="bd805-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd805-111">Example</span></span>  

 <span data-ttu-id="bd805-112">Bu örnek, <xref:System.Linq.Queryable.Concat%2A> tüm `Customer` ve `Employee` ad ve telefon numarası eşlemelerinin bir dizisini döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd805-112">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="bd805-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd805-113">See also</span></span>

- [<span data-ttu-id="bd805-114">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="bd805-114">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="bd805-115">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="bd805-115">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
