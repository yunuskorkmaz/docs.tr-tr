---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir hizmet Işlemi tanımlama (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: hizmet Işlemi tanımlama (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: 9fcad3a31ea5b439c248ba103cbf4ddd75b8109a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765626"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="128ca-103">Nasıl yapılır: hizmet Işlemi tanımlama (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="128ca-103">How to: Define a Service Operation (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="128ca-104">WCF Veri Hizmetleri sunucuda hizmet işlemleri olarak tanımlanan yöntemleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="128ca-104">WCF Data Services expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="128ca-105">Hizmet işlemleri bir veri hizmetinin, sunucuda tanımlı bir yönteme URI aracılığıyla erişim sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="128ca-105">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="128ca-106">Bir hizmet işlemi tanımlamak için, [ `WebGet]` veya `[WebInvoke]` özniteliğini metoduna uygulayın.</span><span class="sxs-lookup"><span data-stu-id="128ca-106">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="128ca-107">Sorgu işleçlerini desteklemek için, hizmet işleminin bir örnek döndürmesi gerekir <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="128ca-107">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="128ca-108">Hizmet işlemleri, içindeki özelliği aracılığıyla temel alınan veri kaynağına erişebilir <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> <xref:System.Data.Services.DataService%601> .</span><span class="sxs-lookup"><span data-stu-id="128ca-108">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="128ca-109">Daha fazla bilgi için bkz. [hizmet işlemleri](service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="128ca-109">For more information, see [Service Operations](service-operations-wcf-data-services.md).</span></span>

<span data-ttu-id="128ca-110">Bu konudaki örnek, `GetOrdersByCity` filtrelenmiş bir <xref:System.Linq.IQueryable%601> örneği `Orders` ve ilgili nesneleri döndüren adlı bir hizmet işlemini tanımlar `Order_Details` .</span><span class="sxs-lookup"><span data-stu-id="128ca-110">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="128ca-111">Örnek, <xref:System.Data.Objects.ObjectContext> Northwind örnek veri hizmeti için veri kaynağı olan örneğe erişir.</span><span class="sxs-lookup"><span data-stu-id="128ca-111">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="128ca-112">Bu hizmet, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="128ca-112">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="128ca-113">Northwind Data Service 'te bir hizmet işlemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="128ca-113">To define a service operation in the Northwind data service</span></span>

1. <span data-ttu-id="128ca-114">Northwind Data Service projesinde, Northwind. svc dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="128ca-114">In the Northwind data service project, open the Northwind.svc file.</span></span>

2. <span data-ttu-id="128ca-115">`Northwind`Sınıfında, aşağıdaki gibi adlı bir hizmet işlemi yöntemi tanımlayın `GetOrdersByCity` :</span><span class="sxs-lookup"><span data-stu-id="128ca-115">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. <span data-ttu-id="128ca-116">`InitializeService` `Northwind` Sınıfının yönteminde, hizmet işlemine erişimi etkinleştirmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="128ca-116">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="128ca-117">GetOrdersByCity hizmeti işlemini sorgulamak için</span><span class="sxs-lookup"><span data-stu-id="128ca-117">To query the GetOrdersByCity service operation</span></span>

- <span data-ttu-id="128ca-118">Bir Web tarayıcısında aşağıdaki örnekte tanımlanan hizmet işlemini çağırmak için aşağıdaki URI 'lerden birini girin:</span><span class="sxs-lookup"><span data-stu-id="128ca-118">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a><span data-ttu-id="128ca-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="128ca-119">Example</span></span>

<span data-ttu-id="128ca-120">Aşağıdaki örnek, Northwind veri hizmetinde adlı bir hizmet işlemi uygular `GetOrderByCity` .</span><span class="sxs-lookup"><span data-stu-id="128ca-120">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="128ca-121">Bu işlem, `Orders` `Order_Details` <xref:System.Linq.IQueryable%601> belirtilen şehir adına göre bir dizi ve ilgili nesneleri örnek olarak döndürmek için ADO.NET Entity Framework kullanır.</span><span class="sxs-lookup"><span data-stu-id="128ca-121">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>

> [!NOTE]
> <span data-ttu-id="128ca-122">Yöntem bir örnek döndürdüğünden, bu hizmet işlemi uç noktasında sorgu işleçleri destekleniyor <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="128ca-122">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a><span data-ttu-id="128ca-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="128ca-123">See also</span></span>

- [<span data-ttu-id="128ca-124">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="128ca-124">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
