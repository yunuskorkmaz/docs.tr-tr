---
title: 'Nasıl yapılır: Intercept Data Service Messages (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: 56e4a3f95c7449ae5693172728c9d777113679bf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101308"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a><span data-ttu-id="0ac9e-102">Nasıl yapılır: Intercept Data Service Messages (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="0ac9e-102">How to: Intercept Data Service Messages (WCF Data Services)</span></span>
<span data-ttu-id="0ac9e-103">İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], işlem için özel mantığı ekleyebilirsiniz, böylece istek iletilerinin yakalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-103">With [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="0ac9e-104">Bir ileti kesmeye data Service'te özel öznitelikli yöntem kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-104">To intercept a message, you use specially attributed methods in the data service.</span></span> <span data-ttu-id="0ac9e-105">Daha fazla bilgi için [dinleyicileri](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="0ac9e-105">For more information, see [Interceptors](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="0ac9e-106">Bu konudaki örnek Northwind örnek veri hizmeti kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-106">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="0ac9e-107">Bu hizmet, tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="0ac9e-107">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a><span data-ttu-id="0ac9e-108">Siparişler varlık kümesi için bir sorgu dinleyiciyi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="0ac9e-108">To define a query interceptor for the Orders entity set</span></span>  
  
1.  <span data-ttu-id="0ac9e-109">Northwind verileri hizmeti projesindeki Northwind.svc dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-109">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="0ac9e-110">Kod sayfasını `Northwind` sınıfında, aşağıdaki `using` deyimi (`Imports` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="0ac9e-110">In the code page for the `Northwind` class, add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3.  <span data-ttu-id="0ac9e-111">İçinde `Northwind` sınıfı, adlandırılan bir hizmet işlemi yöntemi tanımlayın `OnQueryOrders` gibi:</span><span class="sxs-lookup"><span data-stu-id="0ac9e-111">In the `Northwind` class, define a service operation method named `OnQueryOrders` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a><span data-ttu-id="0ac9e-112">Ürünleri varlık kümesi için bir değişiklik dinleyiciyi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="0ac9e-112">To define a change interceptor for the Products entity set</span></span>  
  
1.  <span data-ttu-id="0ac9e-113">Northwind verileri hizmeti projesindeki Northwind.svc dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="0ac9e-114">İçinde `Northwind` sınıfı, adlandırılan bir hizmet işlemi yöntemi tanımlayın `OnChangeProducts` gibi:</span><span class="sxs-lookup"><span data-stu-id="0ac9e-114">In the `Northwind` class, define a service operation method named `OnChangeProducts` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a><span data-ttu-id="0ac9e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ac9e-115">Example</span></span>  
 <span data-ttu-id="0ac9e-116">Bu örnek için bir sorgu dinleyiciyi yöntemi tanımlar `Orders` döndüren bir lambda ifadesi varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-116">This example defines a query interceptor method for the `Orders` entity set that returns a lambda expression.</span></span> <span data-ttu-id="0ac9e-117">Bu ifade istenen filtreleyen bir temsilci içerir `Orders` üzerinde ilgili temel `Customers` belirli bir kişi adına sahip.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-117">This expression contains a delegate that filters the requested `Orders` based on related `Customers` that have a specific contact name.</span></span> <span data-ttu-id="0ac9e-118">Adı, sırayla istekte bulunan kullanıcı göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-118">The name is in turn determined based on the requesting user.</span></span> <span data-ttu-id="0ac9e-119">Bu örnek, veri hizmeti WCF kullanan bir ASP.NET Web uygulamasında barındırılır ve bu kimlik doğrulamasının etkin varsayar.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-119">This example assumes that the data service is hosted within an ASP.NET Web application that uses WCF, and that authentication is enabled.</span></span> <span data-ttu-id="0ac9e-120"><xref:System.Web.HttpContext> Sınıfı, geçerli istek ilkesini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-120">The <xref:System.Web.HttpContext> class is used to retrieve the principle of the current request.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a><span data-ttu-id="0ac9e-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ac9e-121">Example</span></span>  
 <span data-ttu-id="0ac9e-122">Bu örnek için bir değişiklik dinleyiciyi yöntemi tanımlar `Products` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-122">This example defines a change interceptor method for the `Products` entity set.</span></span> <span data-ttu-id="0ac9e-123">Bu yöntem için hizmetine giriş doğrular bir <xref:System.Data.Services.UpdateOperations.Add> veya <xref:System.Data.Services.UpdateOperations.Change> işlemi ve artık sağlanmayan bir ürüne yapılan bir değişikliği bir özel durum başlatır.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-123">This method validates input to the service for an <xref:System.Data.Services.UpdateOperations.Add> or <xref:System.Data.Services.UpdateOperations.Change> operation and raises an exception if a change is being made to a discontinued product.</span></span> <span data-ttu-id="0ac9e-124">Ayrıca, desteklenmeyen bir işlem olarak ürünleri silinmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-124">It also blocks the deletion of products as an unsupported operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a><span data-ttu-id="0ac9e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ac9e-125">See also</span></span>

- [<span data-ttu-id="0ac9e-126">Nasıl yapılır: Hizmet İşlemi Tanımlama</span><span class="sxs-lookup"><span data-stu-id="0ac9e-126">How to: Define a Service Operation</span></span>](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)
- [<span data-ttu-id="0ac9e-127">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="0ac9e-127">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
