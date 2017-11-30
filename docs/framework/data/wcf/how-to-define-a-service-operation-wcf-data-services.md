---
title: "Nasıl yapılır: bir hizmet işlemi (WCF Veri Hizmetleri) tanımlayın"
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
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: feac51c92a7e963d440eefbae94a58b94f49797e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="66e4e-102">Nasıl yapılır: bir hizmet işlemi (WCF Veri Hizmetleri) tanımlayın</span><span class="sxs-lookup"><span data-stu-id="66e4e-102">How to: Define a Service Operation (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="66e4e-103">sunucuda hizmet işlemleri tanımlanan yöntemler kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="66e4e-103"> expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="66e4e-104">Hizmet işlemleri sunucuda tanımlanmış bir yönteme bir URI üzerinden erişim sağlamak için bir veri hizmeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="66e4e-104">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="66e4e-105">Bir hizmet işlemi tanımlamak için uygulama [`WebGet]` veya `[WebInvoke]` özniteliği yöntemi.</span><span class="sxs-lookup"><span data-stu-id="66e4e-105">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="66e4e-106">Sorgu işleçleri desteklemek için hizmet işlemi döndürmelidir bir <xref:System.Linq.IQueryable%601> örneği.</span><span class="sxs-lookup"><span data-stu-id="66e4e-106">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="66e4e-107">Hizmet işlemleri, altta yatan veri kaynağını aracılığıyla erişebilir <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> özelliği <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="66e4e-107">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="66e4e-108">Daha fazla bilgi için bkz: [hizmet işlemleri](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="66e4e-108">For more information, see [Service Operations](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="66e4e-109">Bu konudaki örnek adlı bir hizmet işlemi tanımlar `GetOrdersByCity` bir filtre uygulanmış döndüren <xref:System.Linq.IQueryable%601> örneğini `Orders` ve ilgili `Order_Details` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="66e4e-109">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="66e4e-110">Örnek erişen <xref:System.Data.Objects.ObjectContext> Northwind örnek veri hizmeti için veri kaynağı örneği.</span><span class="sxs-lookup"><span data-stu-id="66e4e-110">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="66e4e-111">Bu hizmeti tamamladığınızda oluşturulan [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="66e4e-111">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="66e4e-112">Northwind veri hizmetinde bir hizmet işlemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="66e4e-112">To define a service operation in the Northwind data service</span></span>  
  
1.  <span data-ttu-id="66e4e-113">Northwind veri hizmeti projesi Northwind.svc dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="66e4e-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="66e4e-114">İçinde `Northwind` sınıfı, adlı bir hizmet işlemi yöntemi tanımlayın `GetOrdersByCity` gibi:</span><span class="sxs-lookup"><span data-stu-id="66e4e-114">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  <span data-ttu-id="66e4e-115">İçinde `InitializeService` yöntemi `Northwind` sınıfı, hizmet işlemi erişimi etkinleştirmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="66e4e-115">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="66e4e-116">Sorgu GetOrdersByCity hizmet işlemi</span><span class="sxs-lookup"><span data-stu-id="66e4e-116">To query the GetOrdersByCity service operation</span></span>  
  
-   <span data-ttu-id="66e4e-117">Bir Web tarayıcısında aşağıdaki örnekte tanımlanan hizmet işlemini çağırmak için aşağıdaki URI'ler birini girin:</span><span class="sxs-lookup"><span data-stu-id="66e4e-117">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a><span data-ttu-id="66e4e-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="66e4e-118">Example</span></span>  
 <span data-ttu-id="66e4e-119">Aşağıdaki örnek adlı bir hizmet işlemi uygulayan `GetOrderByCity` Northwind veri hizmeti.</span><span class="sxs-lookup"><span data-stu-id="66e4e-119">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="66e4e-120">Bu işlem bir dizi dönmek için ADO.NET Entity Framework kullanan `Orders` ve ilgili `Order_Details` olarak nesneleri bir <xref:System.Linq.IQueryable%601> örnek tabanlı üzerinde sağlanan şehir adı.</span><span class="sxs-lookup"><span data-stu-id="66e4e-120">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66e4e-121">Sorgu işleçleri, bu hizmet işlemi noktadaki desteklenir, yöntem döndürdüğünden bir <xref:System.Linq.IQueryable%601> örneği.</span><span class="sxs-lookup"><span data-stu-id="66e4e-121">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a><span data-ttu-id="66e4e-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66e4e-122">See Also</span></span>  
 [<span data-ttu-id="66e4e-123">WCF veri hizmetleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="66e4e-123">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
