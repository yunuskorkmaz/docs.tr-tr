---
title: 'Nasıl yapılır: Ne Kadar İlgili Verilerin Alındığını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: dd59c09185eab003274614dcc30393b060e6b7c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904481"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="c436e-102">Nasıl yapılır: Ne Kadar İlgili Verilerin Alındığını Denetleme</span><span class="sxs-lookup"><span data-stu-id="c436e-102">How to: Control How Much Related Data Is Retrieved</span></span>
<span data-ttu-id="c436e-103">Kullanım <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> ilgili ana hedefiniz için hangi verileri belirtmek için yöntem aynı zamanda alınan.</span><span class="sxs-lookup"><span data-stu-id="c436e-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="c436e-104">Örneğin, müşteri siparişlerinin hakkında bilgi gerekir biliyorsanız, kullanabileceğiniz <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> sipariş bilgileri, aynı zamanda müşteri bilgileri alınır emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="c436e-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="c436e-105">Bu yaklaşım yalnızca bir dönüş içinde iki bilgi veritabanına sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="c436e-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c436e-106">Müşteriler hedeflediğinizde siparişleri alma gibi bir büyük projeksiyon olarak çapraz ürün alarak sorgunuzun ana hedef ilgili veri alabilir.</span><span class="sxs-lookup"><span data-stu-id="c436e-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="c436e-107">Ancak, bu yaklaşım genellikle dezavantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="c436e-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="c436e-108">Örneğin, tahminler ve olmayan değiştirilebilir ve tarafından kalıcı varlıklar sonucu olan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c436e-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="c436e-109">Ve çok sayıda gereksinim duymadığınız veriden alma.</span><span class="sxs-lookup"><span data-stu-id="c436e-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c436e-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="c436e-110">Example</span></span>  
 <span data-ttu-id="c436e-111">Aşağıdaki örnekte, tüm `Orders` tüm `Customers` Londra'da bulunan alınır sorgu yürütüldüğünde.</span><span class="sxs-lookup"><span data-stu-id="c436e-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="c436e-112">Sonuç olarak, art arda gelen erişimi `Orders` özelliği bir `Customer` nesne yeni bir veritabanı sorgusu tetiklemez.</span><span class="sxs-lookup"><span data-stu-id="c436e-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c436e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c436e-113">See also</span></span>

- [<span data-ttu-id="c436e-114">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="c436e-114">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
