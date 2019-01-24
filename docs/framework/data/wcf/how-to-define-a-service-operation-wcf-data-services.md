---
title: 'Nasıl yapılır: Bir hizmet işlemi (WCF Veri Hizmetleri) tanımlayın'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: fffc0efaea200a7b0aa26b0f273b3c0d99338bfb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586559"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="c269a-102">Nasıl yapılır: Bir hizmet işlemi (WCF Veri Hizmetleri) tanımlayın</span><span class="sxs-lookup"><span data-stu-id="c269a-102">How to: Define a Service Operation (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="c269a-103">sunucuda hizmet işlemleri tanımlanmış olan yöntemleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="c269a-103">expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="c269a-104">Hizmet işlemlerine izin ver sunucuda tanımlı bir yönteme bir URI aracılığıyla erişim sağlamak bir veri hizmeti.</span><span class="sxs-lookup"><span data-stu-id="c269a-104">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="c269a-105">Bir hizmet işlemi tanımlamak için uygulama [`WebGet]` veya `[WebInvoke]` özniteliğini yöntemine.</span><span class="sxs-lookup"><span data-stu-id="c269a-105">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="c269a-106">Sorgu işleçleri desteklemek için hizmet işlemi döndürmelidir bir <xref:System.Linq.IQueryable%601> örneği.</span><span class="sxs-lookup"><span data-stu-id="c269a-106">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="c269a-107">Hizmet işlemleri, temel alınan veri kaynağı aracılığıyla erişebilir <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> özellikte <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="c269a-107">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="c269a-108">Daha fazla bilgi için [hizmet işlemleri](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="c269a-108">For more information, see [Service Operations](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="c269a-109">Bu konudaki örnek adlı bir hizmet işlemi tanımlar `GetOrdersByCity` filtrelenmiş bir döndüren <xref:System.Linq.IQueryable%601> örneğini `Orders` ve ilgili `Order_Details` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c269a-109">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="c269a-110">Erişen örnek <xref:System.Data.Objects.ObjectContext> Northwind örnek veri hizmeti için veri kaynağı örneği.</span><span class="sxs-lookup"><span data-stu-id="c269a-110">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="c269a-111">Bu hizmet, tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="c269a-111">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="c269a-112">Northwind veri hizmetinde bir hizmet işlemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="c269a-112">To define a service operation in the Northwind data service</span></span>  
  
1.  <span data-ttu-id="c269a-113">Northwind verileri hizmeti projesindeki Northwind.svc dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="c269a-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="c269a-114">İçinde `Northwind` sınıfı, adlandırılan bir hizmet işlemi yöntemi tanımlayın `GetOrdersByCity` gibi:</span><span class="sxs-lookup"><span data-stu-id="c269a-114">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  <span data-ttu-id="c269a-115">İçinde `InitializeService` yöntemi `Northwind` sınıf, hizmet işlemi erişimi etkinleştirmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c269a-115">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="c269a-116">Sorgu GetOrdersByCity hizmet işlemi</span><span class="sxs-lookup"><span data-stu-id="c269a-116">To query the GetOrdersByCity service operation</span></span>  
  
-   <span data-ttu-id="c269a-117">Bir Web tarayıcısında aşağıdaki örnekte tanımlanan hizmet işlemini çağırmak için aşağıdaki bir URI'leri birini girin:</span><span class="sxs-lookup"><span data-stu-id="c269a-117">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a><span data-ttu-id="c269a-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="c269a-118">Example</span></span>  
 <span data-ttu-id="c269a-119">Aşağıdaki örnekte adlı bir hizmet işlemlerinizi `GetOrderByCity` Northwind verileri hizmeti üzerinde.</span><span class="sxs-lookup"><span data-stu-id="c269a-119">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="c269a-120">Bu işlem, bir dizi döndürmek için ADO.NET varlık çerçevesi kullanır. `Orders` ve ilgili `Order_Details` olarak nesneleri bir <xref:System.Linq.IQueryable%601> örnek tabanlı üzerinde sağlanan şehir adı.</span><span class="sxs-lookup"><span data-stu-id="c269a-120">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c269a-121">Sorgu işleçleri, bu hizmet işlemi uç noktasında desteklenir, yöntemin döndürdüğü için bir <xref:System.Linq.IQueryable%601> örneği.</span><span class="sxs-lookup"><span data-stu-id="c269a-121">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a><span data-ttu-id="c269a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c269a-122">See also</span></span>
- [<span data-ttu-id="c269a-123">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="c269a-123">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
