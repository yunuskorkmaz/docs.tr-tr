---
title: İki dizileri birleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: c0a6dde667c4f858d8177dc80a726619f463f3a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354059"
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="de1aa-102">İki dizileri birleştirme</span><span class="sxs-lookup"><span data-stu-id="de1aa-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="de1aa-103">Kullanım <xref:System.Linq.Queryable.Concat%2A> iki sıraları birleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="de1aa-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="de1aa-104"><xref:System.Linq.Queryable.Concat%2A> İşleci alıcı ve bağımsız değişkeni siparişleri bulunduğu aynı sıralı multisets için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="de1aa-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="de1aa-105">Sonuçları üretilen önce SQL'de sıralama son adımdır.</span><span class="sxs-lookup"><span data-stu-id="de1aa-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="de1aa-106">Bu nedenle, <xref:System.Linq.Queryable.Concat%2A> işleci kullanılarak gerçekleştirilen `UNION ALL` ve bağımsız değişkenlerini sırasını korumaz.</span><span class="sxs-lookup"><span data-stu-id="de1aa-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="de1aa-107">Sıralama emin olmak için sonuçları doğru olduğundan, açıkça sonuçları sıralamak emin olun.</span><span class="sxs-lookup"><span data-stu-id="de1aa-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de1aa-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="de1aa-108">Example</span></span>  
 <span data-ttu-id="de1aa-109">Bu örnekte <xref:System.Linq.Queryable.Concat%2A> tüm bir dizi döndürülecek `Customer` ve `Employee` telefon ve Faks numaraları.</span><span class="sxs-lookup"><span data-stu-id="de1aa-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="de1aa-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="de1aa-110">Example</span></span>  
 <span data-ttu-id="de1aa-111">Bu örnekte <xref:System.Linq.Queryable.Concat%2A> tüm bir dizi döndürülecek `Customer` ve `Employee` adı ve telefon numarası eşlemeleri.</span><span class="sxs-lookup"><span data-stu-id="de1aa-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="de1aa-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de1aa-112">See Also</span></span>  
 [<span data-ttu-id="de1aa-113">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="de1aa-113">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="de1aa-114">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="de1aa-114">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
