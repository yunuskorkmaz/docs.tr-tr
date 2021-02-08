---
description: 'Hakkında daha fazla bilgi edinin: bir dizideki herhangi bir öğenin veya tüm öğelerin bir koşulu karşılayıp karşılamadığını belirleme'
title: Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: a46cf7e4e213eba830dc203f9266a408103cee80
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786114"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="d0ed5-103">Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="d0ed5-103">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>

<span data-ttu-id="d0ed5-104"><xref:System.Linq.Enumerable.All%2A>İşleci bir `true` dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0ed5-104">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="d0ed5-105"><xref:System.Linq.Queryable.Any%2A>İşleci, `true` bir dizideki herhangi bir öğe bir koşulu karşılıyorsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0ed5-105">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0ed5-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0ed5-106">Example</span></span>  

 <span data-ttu-id="d0ed5-107">Aşağıdaki örnek, en az bir siparişi olan müşteriler dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0ed5-107">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="d0ed5-108">`Where` / `where` Yan tümcesi, verilen varsa öğesini değerlendirir `true` `Customer` `Order` .</span><span class="sxs-lookup"><span data-stu-id="d0ed5-108">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="d0ed5-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0ed5-109">Example</span></span>  

 <span data-ttu-id="d0ed5-110">Aşağıdaki Visual Basic kod, sipariş yerleştirmediğiniz müşterilerin listesini belirler ve bu listedeki her müşteri için bir kişi adı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d0ed5-110">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="d0ed5-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0ed5-111">Example</span></span>  

 <span data-ttu-id="d0ed5-112">Aşağıdaki C# örneği, siparişlerinin `ShipCity` "C" ile başlayan bir dizi müşteriyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0ed5-112">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="d0ed5-113">Ayrıca, iadeye dahil olan müşteriler siparişi olmayan müşterilerdir.</span><span class="sxs-lookup"><span data-stu-id="d0ed5-113">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="d0ed5-114">(Tasarıma göre, <xref:System.Linq.Queryable.All%2A> işleç `true` boş bir sıra için döndürülür.) Siparişi olmayan müşteriler, işletmen kullanılarak konsol çıkışında ortadan kalkar `Count` .</span><span class="sxs-lookup"><span data-stu-id="d0ed5-114">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="d0ed5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0ed5-115">See also</span></span>

- [<span data-ttu-id="d0ed5-116">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="d0ed5-116">Query Examples</span></span>](query-examples.md)
