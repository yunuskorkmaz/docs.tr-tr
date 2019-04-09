---
title: 'Nasıl yapılır: Yansıma sağlayıcısı (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 70f232bb510ebfcd125a699f434cd1deea9f8a64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172698"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="b9b3b-102">Nasıl yapılır: Yansıma sağlayıcısı (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9b3b-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="b9b3b-103">Bu sınıfların uygulayan nesneler sunulan sürece, rastgele sınıflara göre bir veri modeli tanımlamanızı sağlayan <xref:System.Linq.IQueryable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b9b3b-103">enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="b9b3b-104">Daha fazla bilgi için [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b9b3b-104">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9b3b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9b3b-105">Example</span></span>  
 <span data-ttu-id="b9b3b-106">Aşağıdaki örnek tanımlar içeren bir veri modeli `Orders` ve `Items`.</span><span class="sxs-lookup"><span data-stu-id="b9b3b-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="b9b3b-107">Varlık kapsayıcı sınıfı `OrderItemData` döndüren iki genel yöntemler olan <xref:System.Linq.IQueryable%601> arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="b9b3b-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="b9b3b-108">Bu arabirimler varlık kümeleridir `Orders` ve `Items` varlık türleri.</span><span class="sxs-lookup"><span data-stu-id="b9b3b-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="b9b3b-109">Bir `Order` birden çok içerebilir `Items`, bu nedenle `Orders` varlık türüne sahip bir `Items` koleksiyonunu döndüren bir gezinti özelliği `Items` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b9b3b-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="b9b3b-110">`OrderItemData` Varlık kapsayıcı sınıfı genel türü, <xref:System.Data.Services.DataService%601> sınıfı `OrderItems` veri hizmeti türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b9b3b-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9b3b-111">Bu örnek, bir bellek içi veri sağlayıcısı gösterir ve geçerli nesne örneklerini dışında değişiklikler kalıcı değildir çünkü uygulama öğesinden türetilmiş herhangi bir avantajı yoktur <xref:System.Data.Services.IUpdatable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b9b3b-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="b9b3b-112">Uygulayan bir örnek <xref:System.Data.Services.IUpdatable> arabirim için bkz: [nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="b9b3b-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria reflection provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria reflection provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="b9b3b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9b3b-113">See also</span></span>

- [<span data-ttu-id="b9b3b-114">Nasıl yapılır: LINQ to SQL Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9b3b-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="b9b3b-115">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="b9b3b-115">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="b9b3b-116">Nasıl yapılır: ADO.NET Entity Framework Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9b3b-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
