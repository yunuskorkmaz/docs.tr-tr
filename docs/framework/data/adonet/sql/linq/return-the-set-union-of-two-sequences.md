---
title: İki sıraları kümesi birleşimini döndürür
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 5aa05384cba826f9cdd7a948a31b2860eaad7f18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358083"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="02ed2-102">İki sıraları kümesi birleşimini döndürür</span><span class="sxs-lookup"><span data-stu-id="02ed2-102">Return the Set Union of Two Sequences</span></span>
<span data-ttu-id="02ed2-103">Kullanım <xref:System.Linq.Queryable.Union%2A> iki sıraları kümesi birleşimi döndürülecek işleci.</span><span class="sxs-lookup"><span data-stu-id="02ed2-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02ed2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="02ed2-104">Example</span></span>  
 <span data-ttu-id="02ed2-105">Bu örnekte <xref:System.Linq.Queryable.Union%2A> tüm ülkelerde, vardır ya da bir dizi döndürülecek `Customers` veya `Employees`.</span><span class="sxs-lookup"><span data-stu-id="02ed2-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="02ed2-106">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Union%2A> işleci için multisets multisets sırasız birleştirme tanımlanır (sonucu etkili bir şekilde `UNION ALL` SQL yan tümcesinde).</span><span class="sxs-lookup"><span data-stu-id="02ed2-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the `UNION ALL` clause in SQL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ed2-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02ed2-107">See Also</span></span>  
 [<span data-ttu-id="02ed2-108">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="02ed2-108">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="02ed2-109">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="02ed2-109">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
