---
title: 'Nasıl yapılır: Hizmet Işlemi tanımlama (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: 3154fadeda400440f68a184b430b7ff15a02203d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780078"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="5334d-102">Nasıl yapılır: Hizmet Işlemi tanımlama (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="5334d-102">How to: Define a Service Operation (WCF Data Services)</span></span>

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="5334d-103">sunucusunda hizmet işlemleri olarak tanımlanan yöntemleri kullanıma sunun.</span><span class="sxs-lookup"><span data-stu-id="5334d-103">expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="5334d-104">Hizmet işlemleri bir veri hizmetinin, sunucuda tanımlı bir yönteme URI aracılığıyla erişim sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="5334d-104">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="5334d-105">Bir hizmet işlemi tanımlamak için, [`WebGet]` veya `[WebInvoke]` özniteliğini metoduna uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5334d-105">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="5334d-106">Sorgu işleçlerini desteklemek için, hizmet işleminin bir <xref:System.Linq.IQueryable%601> örnek döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5334d-106">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="5334d-107">Hizmet işlemleri, <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> <xref:System.Data.Services.DataService%601>içindeki özelliği aracılığıyla temel alınan veri kaynağına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="5334d-107">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="5334d-108">Daha fazla bilgi için bkz. [hizmet işlemleri](service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="5334d-108">For more information, see [Service Operations](service-operations-wcf-data-services.md).</span></span>

<span data-ttu-id="5334d-109">Bu `GetOrdersByCity` konudaki örnek, filtrelenmiş <xref:System.Linq.IQueryable%601> bir örneği `Orders` ve ilgili `Order_Details` nesneleri döndüren adlı bir hizmet işlemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5334d-109">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="5334d-110">Örnek, Northwind örnek <xref:System.Data.Objects.ObjectContext> veri hizmeti için veri kaynağı olan örneğe erişir.</span><span class="sxs-lookup"><span data-stu-id="5334d-110">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="5334d-111">Bu hizmet, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5334d-111">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="5334d-112">Northwind Data Service 'te bir hizmet işlemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="5334d-112">To define a service operation in the Northwind data service</span></span>

1. <span data-ttu-id="5334d-113">Northwind Data Service projesinde, Northwind. svc dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="5334d-113">In the Northwind data service project, open the Northwind.svc file.</span></span>

2. <span data-ttu-id="5334d-114">Sınıfında, aşağıdaki gibi adlı `GetOrdersByCity` bir hizmet işlemi yöntemi tanımlayın: `Northwind`</span><span class="sxs-lookup"><span data-stu-id="5334d-114">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. <span data-ttu-id="5334d-115">`Northwind` Sınıfının yönteminde, hizmet işlemine erişimi etkinleştirmek için aşağıdaki kodu ekleyin: `InitializeService`</span><span class="sxs-lookup"><span data-stu-id="5334d-115">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="5334d-116">GetOrdersByCity hizmeti işlemini sorgulamak için</span><span class="sxs-lookup"><span data-stu-id="5334d-116">To query the GetOrdersByCity service operation</span></span>

- <span data-ttu-id="5334d-117">Bir Web tarayıcısında aşağıdaki örnekte tanımlanan hizmet işlemini çağırmak için aşağıdaki URI 'lerden birini girin:</span><span class="sxs-lookup"><span data-stu-id="5334d-117">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a><span data-ttu-id="5334d-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="5334d-118">Example</span></span>

<span data-ttu-id="5334d-119">Aşağıdaki örnek, Northwind veri hizmetinde adlı `GetOrderByCity` bir hizmet işlemi uygular.</span><span class="sxs-lookup"><span data-stu-id="5334d-119">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="5334d-120">Bu işlem, belirtilen şehir adına göre bir dizi `Orders` ve ilgili `Order_Details` nesneleri <xref:System.Linq.IQueryable%601> örnek olarak döndürmek için ADO.NET Entity Framework kullanır.</span><span class="sxs-lookup"><span data-stu-id="5334d-120">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>

> [!NOTE]
> <span data-ttu-id="5334d-121">Yöntem bir <xref:System.Linq.IQueryable%601> örnek döndürdüğünden, bu hizmet işlemi uç noktasında sorgu işleçleri destekleniyor.</span><span class="sxs-lookup"><span data-stu-id="5334d-121">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a><span data-ttu-id="5334d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5334d-122">See also</span></span>

- [<span data-ttu-id="5334d-123">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="5334d-123">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
