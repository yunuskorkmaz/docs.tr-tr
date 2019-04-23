---
title: Dinleyiciler (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: 17926e144fae206d702c2bcb4f88dd2093442ed5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517908"
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="561e2-102">Dinleyiciler (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="561e2-102">Interceptors (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="561e2-103">bir uygulamanın işlem için özel mantığı ekleyebilirsiniz, böylece istek iletileri izlemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="561e2-103">enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="561e2-104">Gelen iletiler verileri doğrulamak için bu özel mantığı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="561e2-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="561e2-105">Bir sorgu isteğinin kapsamı gibi istek başına bir özel yetkilendirme ilkesi eklemek için kısıtlamanız için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="561e2-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="561e2-106">Durdurma data Service'te özel öznitelikli yöntem tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="561e2-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="561e2-107">Bu yöntemleri çağıran [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ileti işleme uygun noktaya.</span><span class="sxs-lookup"><span data-stu-id="561e2-107">These methods are called by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] at the appropriate point in message processing.</span></span> <span data-ttu-id="561e2-108">Kesiciler varlık kümesi olarak tanımlanır ve hizmet işlemleri gibi dinleyiciyi yöntemleri İstek parametreleri kabul edemez.</span><span class="sxs-lookup"><span data-stu-id="561e2-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="561e2-109">Bir HTTP GET isteği işlerken, sorgu dinleyiciyi yöntemleri, dinleyiciyi'nın varlık örneğini ayarlanmış olup olmadığını belirleyen bir lambda ifadesi, sorgu sonuçları döndürülmelidir döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="561e2-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="561e2-110">Bu ifade, istenen işlem iyice daraltmak için veri hizmeti tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="561e2-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="561e2-111">Aşağıda bir örnek sorgu dinleyiciyi tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="561e2-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="561e2-112">Daha fazla bilgi için [nasıl yapılır: Veri hizmeti iletilerini ıntercept](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="561e2-112">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="561e2-113">Sorgu olmayan işlemleri işlerken olarak adlandırılan, değişiklik dinleyicileri döndürmelidir `void` (`Nothing` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="561e2-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="561e2-114">Değişiklik dinleyiciyi yöntemleri, aşağıdaki iki parametreyi kabul etmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="561e2-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1. <span data-ttu-id="561e2-115">Varlık kümesinin varlık türüyle uyumlu bir tür parametresi.</span><span class="sxs-lookup"><span data-stu-id="561e2-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="561e2-116">Veri Hizmeti değişiklik dinleyiciyi çağırdığında, bu parametrenin değeri istek tarafından gönderilen varlık bilgilerini ücreti yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="561e2-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2. <span data-ttu-id="561e2-117">Türünde bir parametre <xref:System.Data.Services.UpdateOperations>.</span><span class="sxs-lookup"><span data-stu-id="561e2-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="561e2-118">Bu parametrenin değeri, veri hizmeti değişiklik dinleyiciyi çağırdığında, isteği gerçekleştirmeye çalışan işlemi ücreti yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="561e2-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="561e2-119">Bir değişiklik dinleyiciyi bir örneğin tanımı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="561e2-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="561e2-120">Daha fazla bilgi için [nasıl yapılır: Veri hizmeti iletilerini ıntercept](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="561e2-120">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="561e2-121">Aşağıdaki öznitelikler durdurma için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="561e2-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="561e2-122">**[QueryInterceptor (** *EntitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="561e2-122">**[QueryInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="561e2-123">Yöntemleriyle <xref:System.Data.Services.QueryInterceptorAttribute> uygulanan öznitelik kaynak hedef varlık kümesi için bir HTTP GET isteği alındığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="561e2-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="561e2-124">Bu yöntemlerin her zaman biçiminde bir lambda ifadesi döndürmelidir `Expression<Func<T,bool>>`.</span><span class="sxs-lookup"><span data-stu-id="561e2-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="561e2-125">**[ChangeInterceptor (** *EntitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="561e2-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="561e2-126">Yöntemleriyle <xref:System.Data.Services.ChangeInterceptorAttribute> uygulanan öznitelik kaynak hedef varlık kümesi için bir HTTP GET isteği dışındaki HTTP isteği alındığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="561e2-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="561e2-127">Bu yöntemlerin her zaman döndürmelidir `void` (`Nothing` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="561e2-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="561e2-128">Daha fazla bilgi için [nasıl yapılır: Veri hizmeti iletilerini ıntercept](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="561e2-128">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="561e2-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="561e2-129">See also</span></span>

- [<span data-ttu-id="561e2-130">Hizmet İşlemleri</span><span class="sxs-lookup"><span data-stu-id="561e2-130">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)
