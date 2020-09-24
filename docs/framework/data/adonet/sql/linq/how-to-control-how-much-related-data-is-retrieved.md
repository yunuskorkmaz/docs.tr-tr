---
title: 'Nasıl yapılır: Ne Kadar İlgili Verilerin Alındığını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 77ac29eeeaa30ef438b635364dc8e883a0e4c158
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161340"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="66443-102">Nasıl yapılır: Ne Kadar İlgili Verilerin Alındığını Denetleme</span><span class="sxs-lookup"><span data-stu-id="66443-102">How to: Control How Much Related Data Is Retrieved</span></span>

<span data-ttu-id="66443-103"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>Ana Hedefinizdeki ilgili verilerin aynı anda alınması gereken verileri belirtmek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="66443-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="66443-104">Örneğin, müşterilerin siparişleriyle ilgili bilgilere ihtiyacınız olduğunu biliyorsanız, <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> sipariş bilgilerinin Müşteri bilgileriyle aynı zamanda alındığından emin olmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66443-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="66443-105">Bu yaklaşım, her iki bilgi kümesi için yalnızca bir seyahat veritabanına neden olur.</span><span class="sxs-lookup"><span data-stu-id="66443-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66443-106">Bir mimariler, müşterileri hedefleyerek siparişleri alma gibi bir büyük projeksiyon olarak bir çapraz ürün alarak, sorgunuzun ana hedefle ilgili verileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66443-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="66443-107">Ancak bu yaklaşım genellikle dezavantajlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="66443-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="66443-108">Örneğin, sonuçlar yalnızca tahmindir ve tarafından değiştirilebilecek ve kalıcı hale kullanılabilecek varlıklardır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="66443-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="66443-109">Ve ihtiyacınız olmayan çok fazla veri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66443-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66443-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="66443-110">Example</span></span>  

 <span data-ttu-id="66443-111">Aşağıdaki örnekte, `Orders` `Customers` Londra 'da bulunan tüm kullanıcılar için, sorgu yürütüldüğünde alınır.</span><span class="sxs-lookup"><span data-stu-id="66443-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="66443-112">Sonuç olarak, `Orders` bir nesnedeki özelliğe art arda erişim `Customer` Yeni bir veritabanı sorgusu tetiklemez.</span><span class="sxs-lookup"><span data-stu-id="66443-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="66443-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66443-113">See also</span></span>

- [<span data-ttu-id="66443-114">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="66443-114">Querying the Database</span></span>](querying-the-database.md)
