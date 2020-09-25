---
title: Yakalayıcılar (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: 64c5c82f33daf677e58d49655897c392f1f7b7f9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204404"
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="764ba-102">Yakalayıcılar (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="764ba-102">Interceptors (WCF Data Services)</span></span>

<span data-ttu-id="764ba-103">WCF Veri Hizmetleri bir uygulamaya özel mantık ekleyebilmeniz için, bir uygulamanın istek iletilerini ele almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="764ba-103">WCF Data Services enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="764ba-104">Gelen iletilerdeki verileri doğrulamak için bu özel mantığı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="764ba-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="764ba-105">Ayrıca, istek başına özel bir yetkilendirme ilkesi eklemek gibi bir sorgu isteğinin kapsamını kısıtlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="764ba-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="764ba-106">Yakatasyon, veri hizmetindeki özel olarak öznitelikli yöntemler tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="764ba-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="764ba-107">Bu yöntemler ileti işleme uygun noktasında WCF Veri Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="764ba-107">These methods are called by WCF Data Services at the appropriate point in message processing.</span></span> <span data-ttu-id="764ba-108">Yakalayıcılar, varlık başına ayarlanan temelinde tanımlanır ve bakım yöntemleri, hizmet işlemleri gibi istekten parametreleri kabul edemez.</span><span class="sxs-lookup"><span data-stu-id="764ba-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="764ba-109">Bir HTTP GET isteği işlenirken çağrılan sorgu yakalayıcısı yöntemleri, bir yakacının varlık kümesi örneğinin sorgu sonuçları tarafından döndürülüp döndürülmeyeceğini belirleyen bir lambda ifadesi döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="764ba-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="764ba-110">Bu ifade, istenen işlemi daha fazla iyileştirmek için veri hizmeti tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="764ba-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="764ba-111">Aşağıda sorgu yakalayıcısı 'nın örnek bir tanımı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="764ba-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="764ba-112">Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti Iletilerini kesme](how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="764ba-112">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="764ba-113">Sorgu olmayan işlemler işlenirken çağrılan, değişiklik dinleyicileri `void` ( `Nothing` Visual Basic) döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="764ba-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="764ba-114">Değişiklik yakalayıcısı metotları aşağıdaki iki parametreyi kabul etmelidir:</span><span class="sxs-lookup"><span data-stu-id="764ba-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1. <span data-ttu-id="764ba-115">Varlık kümesinin varlık türü ile uyumlu olan bir türün parametresi.</span><span class="sxs-lookup"><span data-stu-id="764ba-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="764ba-116">Veri hizmeti değişiklik yakalayıcısını istediğinde, bu parametrenin değeri istek tarafından gönderilen varlık bilgilerini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="764ba-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2. <span data-ttu-id="764ba-117">Türünde bir parametre <xref:System.Data.Services.UpdateOperations> .</span><span class="sxs-lookup"><span data-stu-id="764ba-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="764ba-118">Veri hizmeti değişiklik yakalayıcısını istediğinde, bu parametrenin değeri isteğin gerçekleştirmeye çalıştığı işlemi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="764ba-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="764ba-119">Aşağıda, değişiklik yakalayıcısı 'nın örnek bir tanımı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="764ba-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="764ba-120">Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti Iletilerini kesme](how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="764ba-120">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="764ba-121">Aşağıdaki öznitelikler, yakalaşmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="764ba-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="764ba-122">**[Queryyakalayıcısı (** *entitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="764ba-122">**[QueryInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="764ba-123">Özniteliği uygulanmış olan Yöntemler, <xref:System.Data.Services.QueryInterceptorAttribute> hedeflenen varlık kümesi kaynağı için BIR http get isteği alındığında çağırılır.</span><span class="sxs-lookup"><span data-stu-id="764ba-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="764ba-124">Bu yöntemlerin, her zaman biçiminde bir lambda ifadesi döndürmesi gerekir `Expression<Func<T,bool>>` .</span><span class="sxs-lookup"><span data-stu-id="764ba-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="764ba-125">**[Changeyakalayıcısı (** *entitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="764ba-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="764ba-126"><xref:System.Data.Services.ChangeInterceptorAttribute>Hedeflenen varlık kümesi kaynağı IÇIN http get isteği dışında BIR http isteği alındığında, özniteliği uygulanmış metotlar çağırılır.</span><span class="sxs-lookup"><span data-stu-id="764ba-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="764ba-127">Bu yöntemlerin her zaman dönmesi gerekir `void` ( `Nothing` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="764ba-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="764ba-128">Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti Iletilerini kesme](how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="764ba-128">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="764ba-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="764ba-129">See also</span></span>

- [<span data-ttu-id="764ba-130">Hizmet İşlemleri</span><span class="sxs-lookup"><span data-stu-id="764ba-130">Service Operations</span></span>](service-operations-wcf-data-services.md)
