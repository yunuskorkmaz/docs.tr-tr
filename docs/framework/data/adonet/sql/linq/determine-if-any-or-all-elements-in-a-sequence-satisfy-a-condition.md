---
title: Bir dizi veya tamamını öğelerinde bir koşul karşılayıp karşılamadığını belirlemek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: cd910b35f82f816158cb686a283e44e3b8b6b33b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359978"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="90714-102">Bir dizi veya tamamını öğelerinde bir koşul karşılayıp karşılamadığını belirlemek</span><span class="sxs-lookup"><span data-stu-id="90714-102">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>
<span data-ttu-id="90714-103"><xref:System.Linq.Enumerable.All%2A> Operatörü döndürür `true` dizisindeki tüm öğeler bir koşulla eşleşmesi durumunda.</span><span class="sxs-lookup"><span data-stu-id="90714-103">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="90714-104"><xref:System.Linq.Queryable.Any%2A> Operatörü döndürür `true` bir dizisinde herhangi bir öğe koşulu uymazsa.</span><span class="sxs-lookup"><span data-stu-id="90714-104">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90714-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="90714-105">Example</span></span>  
 <span data-ttu-id="90714-106">Aşağıdaki örnekte, en az bir sipariş olan müşterilerin bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="90714-106">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="90714-107">`Where` / `where` Yan tümcesi hesaplar için `true` , verilen `Customer` içeren `Order`.</span><span class="sxs-lookup"><span data-stu-id="90714-107">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="90714-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="90714-108">Example</span></span>  
 <span data-ttu-id="90714-109">Aşağıdaki Visual Basic kodu siparişleri yerleştirilmedi müşteriler listesi belirler ve bu listedeki her müşteri için bir ilgili kişi adı sağlanır sağlar.</span><span class="sxs-lookup"><span data-stu-id="90714-109">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="90714-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="90714-110">Example</span></span>  
 <span data-ttu-id="90714-111">Aşağıdaki C# örnek siparişleri sahip müşteriler bir dizi döndürür bir `ShipCity` "C" ile başlayan.</span><span class="sxs-lookup"><span data-stu-id="90714-111">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="90714-112">Return de dahil hiç siparişi olmayan müşteriler etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="90714-112">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="90714-113">(Tasarıma göre <xref:System.Linq.Queryable.All%2A> operatörü döndürür `true` boş bir dizi için.) Müşteri siparişi ortadan konsol çıktısı kullanarak `Count` işleci.</span><span class="sxs-lookup"><span data-stu-id="90714-113">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="90714-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="90714-114">See Also</span></span>  
 [<span data-ttu-id="90714-115">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="90714-115">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
