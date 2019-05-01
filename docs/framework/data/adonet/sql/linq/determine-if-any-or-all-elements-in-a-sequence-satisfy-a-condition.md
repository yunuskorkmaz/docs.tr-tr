---
title: Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: c1bc8e18f2e3b0c67b98713e67fc261649a6a0e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877376"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="239b1-102">Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="239b1-102">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>
<span data-ttu-id="239b1-103"><xref:System.Linq.Enumerable.All%2A> İşleci döndürür `true` bir dizideki tüm öğeler koşulu karşılaması durumunda.</span><span class="sxs-lookup"><span data-stu-id="239b1-103">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="239b1-104"><xref:System.Linq.Queryable.Any%2A> İşleci döndürür `true` bir dizideki herhangi bir öğenin bir koşulu karşılıyorsa.</span><span class="sxs-lookup"><span data-stu-id="239b1-104">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="239b1-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="239b1-105">Example</span></span>  
 <span data-ttu-id="239b1-106">Aşağıdaki örnek, en az bir sipariş olan müşteriler bir dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="239b1-106">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="239b1-107">`Where` / `where` Yan tümcesi değerlendirilen `true` , verilen `Customer` içeren `Order`.</span><span class="sxs-lookup"><span data-stu-id="239b1-107">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="239b1-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="239b1-108">Example</span></span>  
 <span data-ttu-id="239b1-109">Aşağıdaki Visual Basic kod, sipariş vermiş değil Müşteri listesini belirler ve bu listedeki her müşteri için bir ilgili kişi adı sağlanır sağlar.</span><span class="sxs-lookup"><span data-stu-id="239b1-109">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="239b1-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="239b1-110">Example</span></span>  
 <span data-ttu-id="239b1-111">Aşağıdaki C# örnek müşteri siparişleri olan bir dizi döndürür bir `ShipCity` "C" ile başlayan.</span><span class="sxs-lookup"><span data-stu-id="239b1-111">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="239b1-112">Ayrıca dönüş sipariş olan müşteriler bunlara dahildir.</span><span class="sxs-lookup"><span data-stu-id="239b1-112">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="239b1-113">(Tasarıma göre <xref:System.Linq.Queryable.All%2A> işleci döndürür `true` boş bir dizi için.) Sipariş müşterilerle ortadan konsol çıkışında kullanarak `Count` işleci.</span><span class="sxs-lookup"><span data-stu-id="239b1-113">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="239b1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="239b1-114">See also</span></span>

- [<span data-ttu-id="239b1-115">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="239b1-115">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
