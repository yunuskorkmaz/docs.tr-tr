---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 1c4d131b21c69e11dd6d8b574e4c22a6af7c5a25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766242"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="55645-103">Nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="55645-103">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="55645-104">WCF Veri Hizmetleri, bu sınıflar arabirimini uygulayan nesneler olarak sunulduğunu sürece rastgele sınıflara dayalı bir veri modeli tanımlamanızı sağlar <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="55645-104">WCF Data Services enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="55645-105">Daha fazla bilgi için bkz. [veri hizmetleri sağlayıcıları](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="55645-105">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55645-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="55645-106">Example</span></span>  

 <span data-ttu-id="55645-107">Aşağıdaki örnek, ve içeren bir veri modelini tanımlar `Orders` `Items` .</span><span class="sxs-lookup"><span data-stu-id="55645-107">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="55645-108">Varlık kapsayıcı sınıfında `OrderItemData` arabirimler döndüren iki ortak yöntem vardır <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="55645-108">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="55645-109">Bu arabirimler, `Orders` ve `Items` varlık türlerinin varlık kümeleridir.</span><span class="sxs-lookup"><span data-stu-id="55645-109">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="55645-110">`Order`, Birden çok içerebilir `Items` , bu nedenle `Orders` varlık türünün `Items` bir nesne koleksiyonu döndüren bir gezinti özelliği vardır `Items` .</span><span class="sxs-lookup"><span data-stu-id="55645-110">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="55645-111">`OrderItemData`Varlık kapsayıcı sınıfı, <xref:System.Data.Services.DataService%601> `OrderItems` veri hizmetinin türetildiği sınıfın genel türüdür.</span><span class="sxs-lookup"><span data-stu-id="55645-111">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55645-112">Bu örnekte, bellek içi veri sağlayıcısı ve değişiklikler geçerli nesne örneklerinin dışında kalıcı olmadığından, arabirimi uygulamadan türetilmiş bir avantaj yoktur <xref:System.Data.Services.IUpdatable> .</span><span class="sxs-lookup"><span data-stu-id="55645-112">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="55645-113">Arabirimi uygulayan bir örnek için <xref:System.Data.Services.IUpdatable> bkz. [nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="55645-113">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="55645-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55645-114">See also</span></span>

- [<span data-ttu-id="55645-115">Nasıl yapılır: LINQ to SQL Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="55645-115">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="55645-116">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="55645-116">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="55645-117">Nasıl yapılır: ADO.NET Entity Framework Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="55645-117">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
