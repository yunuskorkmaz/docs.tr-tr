---
title: 'Nasıl yapılır: Yansıma sağlayıcısını (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: feee679c37cd3dafb80021752ee25444c54f0809
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791004"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="fa051-102">Nasıl yapılır: Yansıma sağlayıcısını (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa051-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="fa051-103">, bu sınıfların <xref:System.Linq.IQueryable%601> arabirimini uygulayan nesneler olarak kullanıma sunulduğunu sürece rastgele sınıflara dayalı bir veri modeli tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa051-103">enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="fa051-104">Daha fazla bilgi için bkz. [veri hizmetleri sağlayıcıları](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="fa051-104">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa051-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa051-105">Example</span></span>  
 <span data-ttu-id="fa051-106">Aşağıdaki örnek, ve `Orders` `Items`içeren bir veri modelini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fa051-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="fa051-107">Varlık kapsayıcı sınıfında `OrderItemData` arabirimler döndüren <xref:System.Linq.IQueryable%601> iki ortak yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="fa051-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="fa051-108">Bu arabirimler, `Orders` ve `Items` varlık türlerinin varlık kümeleridir.</span><span class="sxs-lookup"><span data-stu-id="fa051-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="fa051-109">`Items` `Orders` `Items` , Birden çok içerebilir, bu nedenle varlık türünün bir `Items` nesne koleksiyonu döndüren bir gezinti özelliği vardır. `Order`</span><span class="sxs-lookup"><span data-stu-id="fa051-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="fa051-110">Varlık kapsayıcı sınıfı, `OrderItems` veri hizmetinin türetildiği <xref:System.Data.Services.DataService%601> sınıfın genel türüdür. `OrderItemData`</span><span class="sxs-lookup"><span data-stu-id="fa051-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa051-111">Bu örnekte, bellek içi veri sağlayıcısı ve değişiklikler geçerli nesne örneklerinin dışında kalıcı olmadığından, <xref:System.Data.Services.IUpdatable> arabirimi uygulamadan türetilmiş bir avantaj yoktur.</span><span class="sxs-lookup"><span data-stu-id="fa051-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="fa051-112"><xref:System.Data.Services.IUpdatable> Arabirimini uygulayan bir örnek için bkz [. nasıl yapılır: LINQ to SQL veri kaynağı](create-a-data-service-using-linq-to-sql-wcf.md)kullanarak veri hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fa051-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="fa051-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa051-113">See also</span></span>

- [<span data-ttu-id="fa051-114">Nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa051-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="fa051-115">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="fa051-115">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="fa051-116">Nasıl yapılır: Bir ADO.NET Entity Framework veri kaynağı kullanarak veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa051-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
