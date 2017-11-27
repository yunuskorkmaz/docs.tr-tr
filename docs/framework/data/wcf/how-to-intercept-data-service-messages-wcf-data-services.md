---
title: "Nasıl yapılır: müdahale veri hizmeti iletileri (WCF Veri Hizmetleri)"
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
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c18664eaa154fbc048c77cb359d0926f04b7e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a><span data-ttu-id="1ab6d-102">Nasıl yapılır: müdahale veri hizmeti iletileri (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="1ab6d-102">How to: Intercept Data Service Messages (WCF Data Services)</span></span>
<span data-ttu-id="1ab6d-103">İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], böylece bir işlem Özel mantık ekleyebilirsiniz istek iletilerini ele geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-103">With [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="1ab6d-104">Bir ileti müdahale için veri hizmeti özel öznitelikli yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-104">To intercept a message, you use specially attributed methods in the data service.</span></span> <span data-ttu-id="1ab6d-105">Daha fazla bilgi için bkz: [dinleyiciler](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="1ab6d-105">For more information, see [Interceptors](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="1ab6d-106">Bu konudaki örnek Northwind örnek veri hizmeti kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-106">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="1ab6d-107">Bu hizmeti tamamladığınızda oluşturulan [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="1ab6d-107">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a><span data-ttu-id="1ab6d-108">Siparişleri varlık kümesi için sorgu dinleyiciyi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="1ab6d-108">To define a query interceptor for the Orders entity set</span></span>  
  
1.  <span data-ttu-id="1ab6d-109">Northwind veri hizmeti projesi Northwind.svc dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-109">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="1ab6d-110">İçin kod sayfasından `Northwind` sınıfında, aşağıdaki ekleyin `using` deyimi (`Imports` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="1ab6d-110">In the code page for the `Northwind` class, add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3.  <span data-ttu-id="1ab6d-111">İçinde `Northwind` sınıfı, adlı bir hizmet işlemi yöntemi tanımlayın `OnQueryOrders` gibi:</span><span class="sxs-lookup"><span data-stu-id="1ab6d-111">In the `Northwind` class, define a service operation method named `OnQueryOrders` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a><span data-ttu-id="1ab6d-112">Ürünler varlık kümesi için bir değişiklik dinleyiciyi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="1ab6d-112">To define a change interceptor for the Products entity set</span></span>  
  
1.  <span data-ttu-id="1ab6d-113">Northwind veri hizmeti projesi Northwind.svc dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="1ab6d-114">İçinde `Northwind` sınıfı, adlı bir hizmet işlemi yöntemi tanımlayın `OnChangeProducts` gibi:</span><span class="sxs-lookup"><span data-stu-id="1ab6d-114">In the `Northwind` class, define a service operation method named `OnChangeProducts` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a><span data-ttu-id="1ab6d-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ab6d-115">Example</span></span>  
 <span data-ttu-id="1ab6d-116">Bu örnek için bir sorgu dinleyiciyi yöntemi tanımlar `Orders` lambda ifadesi döndürür varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-116">This example defines a query interceptor method for the `Orders` entity set that returns a lambda expression.</span></span> <span data-ttu-id="1ab6d-117">Bu ifade istenen filtreler bir temsilci içerir `Orders` üzerinde ilgili temel `Customers` belirli bir kişi adına sahip.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-117">This expression contains a delegate that filters the requested `Orders` based on related `Customers` that have a specific contact name.</span></span> <span data-ttu-id="1ab6d-118">Ad sırayla istekte bulunan kullanıcı göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-118">The name is in turn determined based on the requesting user.</span></span> <span data-ttu-id="1ab6d-119">Bu örnek veri hizmeti WCF kullanan bir ASP.NET Web uygulaması içinde barındırılır ve bu kimlik doğrulamasının etkin olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-119">This example assumes that the data service is hosted within an ASP.NET Web application that uses WCF, and that authentication is enabled.</span></span> <span data-ttu-id="1ab6d-120"><xref:System.Web.HttpContext> Sınıfı, geçerli istek ilkesini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-120">The <xref:System.Web.HttpContext> class is used to retrieve the principle of the current request.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a><span data-ttu-id="1ab6d-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ab6d-121">Example</span></span>  
 <span data-ttu-id="1ab6d-122">Bu örnek için bir değişiklik dinleyiciyi yöntemi tanımlar `Products` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-122">This example defines a change interceptor method for the `Products` entity set.</span></span> <span data-ttu-id="1ab6d-123">Bu yöntem için hizmetine giriş doğrular bir <xref:System.Data.Services.UpdateOperations.Add> veya <xref:System.Data.Services.UpdateOperations.Change> işlemi ve devam etmeyen ürüne yapılan bir değişiklik olursa bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-123">This method validates input to the service for an <xref:System.Data.Services.UpdateOperations.Add> or <xref:System.Data.Services.UpdateOperations.Change> operation and raises an exception if a change is being made to a discontinued product.</span></span> <span data-ttu-id="1ab6d-124">Ayrıca, desteklenmeyen bir işlem olarak ürünleri silinmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-124">It also blocks the deletion of products as an unsupported operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a><span data-ttu-id="1ab6d-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ab6d-125">See Also</span></span>  
 [<span data-ttu-id="1ab6d-126">Nasıl yapılır: bir hizmet işlemi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="1ab6d-126">How to: Define a Service Operation</span></span>](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)  
 [<span data-ttu-id="1ab6d-127">WCF veri hizmetleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="1ab6d-127">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
