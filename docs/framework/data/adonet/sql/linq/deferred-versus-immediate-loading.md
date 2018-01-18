---
title: "Ertelenmiş karşı hemen yükleniyor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f40f6c3d94aeeae41c4cce00bac8de863226f287
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="deferred-versus-immediate-loading"></a><span data-ttu-id="43931-102">Ertelenmiş karşı hemen yükleniyor</span><span class="sxs-lookup"><span data-stu-id="43931-102">Deferred versus Immediate Loading</span></span>
<span data-ttu-id="43931-103">Bir nesne için sorgularken gerçekte yalnızca istediğiniz nesnesini alın.</span><span class="sxs-lookup"><span data-stu-id="43931-103">When you query for an object, you actually retrieve only the object you requested.</span></span> <span data-ttu-id="43931-104">*İlgili* nesneleri değil otomatik olarak alınan aynı anda.</span><span class="sxs-lookup"><span data-stu-id="43931-104">The *related* objects are not automatically fetched at the same time.</span></span> <span data-ttu-id="43931-105">(Daha fazla bilgi için bkz: [sorgulama arasında ilişkiler](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) Bunları erişme denemesi bunları alır bir isteği oluşturduğundan ilişkili nesneleri zaten olmayan olgu yüklenmiş göremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="43931-105">(For more information, see [Querying Across Relationships](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) You cannot see the fact that the related objects are not already loaded, because an attempt to access them produces a request that retrieves them.</span></span>  
  
 <span data-ttu-id="43931-106">Örneğin, belirli bir sipariş kümesi için sorgu ve bir e-posta bildirimi belirli müşterilere nadiren göndermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43931-106">For example, you might want to query for a particular set of orders and then only occasionally send an e-mail notification to particular customers.</span></span> <span data-ttu-id="43931-107">Mutlaka Başlangıçta tüm müşteri verilerine her sipariş ile almak ihtiyaç duymaz.</span><span class="sxs-lookup"><span data-stu-id="43931-107">You would not necessarily need initially to retrieve all customer data with every order.</span></span> <span data-ttu-id="43931-108">Ek bilgi alınmasını kesinlikle zorunda kadar erteleme Ertelenen yükleme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43931-108">You can use deferred loading to defer retrieval of extra information until you absolutely have to.</span></span> <span data-ttu-id="43931-109">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="43931-109">Consider the following example:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 <span data-ttu-id="43931-110">Tersi de olabilir.</span><span class="sxs-lookup"><span data-stu-id="43931-110">The opposite might also be true.</span></span> <span data-ttu-id="43931-111">Aynı anda müşteri ve sipariş verilerini görüntülemek için olan bir uygulama olabilir.</span><span class="sxs-lookup"><span data-stu-id="43931-111">You might have an application that has to view customer and order data at the same time.</span></span> <span data-ttu-id="43931-112">Her iki veri kümesini gerektiğini bildirin.</span><span class="sxs-lookup"><span data-stu-id="43931-112">You know you need both sets of data.</span></span> <span data-ttu-id="43931-113">Sonuçlar elde hemen sonra uygulamanızın sipariş bilgilerini her müşteri için gerekiyor. bildiğiniz.</span><span class="sxs-lookup"><span data-stu-id="43931-113">You know your application needs order information for each customer as soon as you get the results.</span></span> <span data-ttu-id="43931-114">Her müşteri için siparişler için tek tek sorgular göndermeye istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="43931-114">You would not want to submit individual queries for orders for every customer.</span></span> <span data-ttu-id="43931-115">Gerçekten istediğiniz müşterilerin birlikte sipariş verileri sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="43931-115">What you really want is to retrieve the order data together with the customers.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 <span data-ttu-id="43931-116">Ayrıca müşteriler ve siparişler bir sorguda çapraz ürün oluşturma ve bir büyük projeksiyon olarak verilerin tüm göreli BITS alma birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43931-116">You can also join customers and orders in a query by forming the cross-product and retrieving all the relative bits of data as one large projection.</span></span> <span data-ttu-id="43931-117">Ancak bu sonuçları varlıklar değildir.</span><span class="sxs-lookup"><span data-stu-id="43931-117">But these results are not entities.</span></span> <span data-ttu-id="43931-118">(Daha fazla bilgi için bkz: [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)).</span><span class="sxs-lookup"><span data-stu-id="43931-118">(For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)).</span></span> <span data-ttu-id="43931-119">Bu sonuçları değişti ve kalıcı tahminleri olur ancak kimlik ve olduğunu değiştirebilirsiniz, nesneleri varlıklardır.</span><span class="sxs-lookup"><span data-stu-id="43931-119">Entities are objects that have identity and that you can modify, whereas these results would be projections that cannot be changed and persisted.</span></span> <span data-ttu-id="43931-120">Her bir müşteri düzleştirilmiş birleştirme çıkış her sırada yinelenir gibi kötüsü, çok fazla yedek veri alma.</span><span class="sxs-lookup"><span data-stu-id="43931-120">Even worse, you would be retrieving lots of redundant data as each customer repeats for each order in the flattened join output.</span></span>  
  
 <span data-ttu-id="43931-121">Gerçekten ihtiyacınız, aynı anda bir dizi ilgili nesneyi almak için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="43931-121">What you really need is a way to retrieve a set of related objects at the same time.</span></span> <span data-ttu-id="43931-122">Hiçbir zaman fazla veya az kullanım amacınız için gerekli olandan alma böylece bir grafik sonuçları bir bölümünü kümesidir.</span><span class="sxs-lookup"><span data-stu-id="43931-122">The set is a delineated section of a graph so that you would never be retrieving more or less than was necessary for your intended use.</span></span> <span data-ttu-id="43931-123">Bu amaçla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sağlar <xref:System.Data.Linq.DataLoadOptions> nesne modeli bölge hemen yüklenmesi için.</span><span class="sxs-lookup"><span data-stu-id="43931-123">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides <xref:System.Data.Linq.DataLoadOptions> for immediate loading of a region of your object model.</span></span> <span data-ttu-id="43931-124">Yöntemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="43931-124">Methods include:</span></span>  
  
-   <span data-ttu-id="43931-125"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Hemen ana hedefe ilgili verileri yüklemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="43931-125">The  <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method, to immediately load data related to the main target.</span></span>  
  
-   <span data-ttu-id="43931-126"><xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> Yöntemine filtre nesneleri için belirli bir ilişkisi alınamadı.</span><span class="sxs-lookup"><span data-stu-id="43931-126">The <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method, to filter objects retrieved for a particular relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43931-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43931-127">See Also</span></span>  
 [<span data-ttu-id="43931-128">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="43931-128">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
