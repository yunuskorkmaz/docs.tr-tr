---
title: "Nasıl yapılır: yansıma sağlayıcısı (WCF Veri Hizmetleri) kullanarak bir veri hizmeti oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11f01a88e1d276321384f00f3e103322ccaef339
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="dd26f-102">Nasıl yapılır: yansıma sağlayıcısı (WCF Veri Hizmetleri) kullanarak bir veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="dd26f-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="dd26f-103">Bu sınıfların uygulayan nesneler sunulan sürece, rasgele sınıflara göre bir veri modeli tanımlamanızı sağlar <xref:System.Linq.IQueryable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="dd26f-103"> enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="dd26f-104">Daha fazla bilgi için bkz: [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="dd26f-104">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd26f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd26f-105">Example</span></span>  
 <span data-ttu-id="dd26f-106">Aşağıdaki örnek içeren bir veri modeli tanımlar `Orders` ve `Items`.</span><span class="sxs-lookup"><span data-stu-id="dd26f-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="dd26f-107">Varlık kapsayıcı sınıfı `OrderItemData` dönüş iki genel yöntemi vardır <xref:System.Linq.IQueryable%601> arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="dd26f-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="dd26f-108">Bu arabirimleri varlık kümeleridir `Orders` ve `Items` varlık türleri.</span><span class="sxs-lookup"><span data-stu-id="dd26f-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="dd26f-109">Bir `Order` birden çok içerebilir `Items`, böylece `Orders` varlık türüne sahip bir `Items` koleksiyonu döndüren bir gezinti özelliği `Items` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="dd26f-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="dd26f-110">`OrderItemData` Varlık kapsayıcı sınıftır genel türü <xref:System.Data.Services.DataService%601> sınıfı `OrderItems` veri hizmeti elde edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dd26f-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd26f-111">Bu örnek, bir bellek içi veri sağlayıcısı gösterir ve değişiklikleri geçerli nesne örneklerini dışında kalıcı değildir çünkü uygulama öğesinden türetilen fayda yoktur <xref:System.Data.Services.IUpdatable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="dd26f-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="dd26f-112">Uygulayan bir örnek <xref:System.Data.Services.IUpdatable> arabirim için bkz: [nasıl yapılır: bir LINQ to SQL veri kaynağı kullanarak bir veri hizmeti oluşturmak](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="dd26f-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria reflection provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria reflection provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="dd26f-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd26f-113">See Also</span></span>  
 [<span data-ttu-id="dd26f-114">Nasıl yapılır: SQL veri kaynağı için bir LINQ kullanarak bir veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="dd26f-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)  
 [<span data-ttu-id="dd26f-115">Veri Hizmetleri sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="dd26f-115">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="dd26f-116">Nasıl yapılır: bir ADO.NET Entity Framework Veri kaynağı kullanarak bir veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="dd26f-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
