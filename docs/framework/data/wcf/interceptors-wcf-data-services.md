---
description: 'Daha fazla bilgi edinin: yakalayıcılar (WCF Veri Hizmetleri)'
title: Yakalayıcılar (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: f73ee498d0419df9e083248802ea52ed050a914b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765080"
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="3d5db-103">Yakalayıcılar (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="3d5db-103">Interceptors (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="3d5db-104">WCF Veri Hizmetleri bir uygulamaya özel mantık ekleyebilmeniz için, bir uygulamanın istek iletilerini ele almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d5db-104">WCF Data Services enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="3d5db-105">Gelen iletilerdeki verileri doğrulamak için bu özel mantığı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d5db-105">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="3d5db-106">Ayrıca, istek başına özel bir yetkilendirme ilkesi eklemek gibi bir sorgu isteğinin kapsamını kısıtlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d5db-106">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="3d5db-107">Yakatasyon, veri hizmetindeki özel olarak öznitelikli yöntemler tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3d5db-107">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="3d5db-108">Bu yöntemler ileti işleme uygun noktasında WCF Veri Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3d5db-108">These methods are called by WCF Data Services at the appropriate point in message processing.</span></span> <span data-ttu-id="3d5db-109">Yakalayıcılar, varlık başına ayarlanan temelinde tanımlanır ve bakım yöntemleri, hizmet işlemleri gibi istekten parametreleri kabul edemez.</span><span class="sxs-lookup"><span data-stu-id="3d5db-109">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="3d5db-110">Bir HTTP GET isteği işlenirken çağrılan sorgu yakalayıcısı yöntemleri, bir yakacının varlık kümesi örneğinin sorgu sonuçları tarafından döndürülüp döndürülmeyeceğini belirleyen bir lambda ifadesi döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="3d5db-110">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="3d5db-111">Bu ifade, istenen işlemi daha fazla iyileştirmek için veri hizmeti tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3d5db-111">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="3d5db-112">Aşağıda sorgu yakalayıcısı 'nın örnek bir tanımı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3d5db-112">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="3d5db-113">Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti Iletilerini kesme](how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="3d5db-113">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="3d5db-114">Sorgu olmayan işlemler işlenirken çağrılan, değişiklik dinleyicileri `void` ( `Nothing` Visual Basic) döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d5db-114">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="3d5db-115">Değişiklik yakalayıcısı metotları aşağıdaki iki parametreyi kabul etmelidir:</span><span class="sxs-lookup"><span data-stu-id="3d5db-115">Change interceptor methods must accept the following two parameters:</span></span>  
  
1. <span data-ttu-id="3d5db-116">Varlık kümesinin varlık türü ile uyumlu olan bir türün parametresi.</span><span class="sxs-lookup"><span data-stu-id="3d5db-116">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="3d5db-117">Veri hizmeti değişiklik yakalayıcısını istediğinde, bu parametrenin değeri istek tarafından gönderilen varlık bilgilerini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="3d5db-117">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2. <span data-ttu-id="3d5db-118">Türünde bir parametre <xref:System.Data.Services.UpdateOperations> .</span><span class="sxs-lookup"><span data-stu-id="3d5db-118">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="3d5db-119">Veri hizmeti değişiklik yakalayıcısını istediğinde, bu parametrenin değeri isteğin gerçekleştirmeye çalıştığı işlemi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="3d5db-119">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="3d5db-120">Aşağıda, değişiklik yakalayıcısı 'nın örnek bir tanımı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3d5db-120">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="3d5db-121">Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti Iletilerini kesme](how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="3d5db-121">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="3d5db-122">Aşağıdaki öznitelikler, yakalaşmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="3d5db-122">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="3d5db-123">**[Queryyakalayıcısı (** *entitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="3d5db-123">**[QueryInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="3d5db-124">Özniteliği uygulanmış olan Yöntemler, <xref:System.Data.Services.QueryInterceptorAttribute> hedeflenen varlık kümesi kaynağı için BIR http get isteği alındığında çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3d5db-124">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="3d5db-125">Bu yöntemlerin, her zaman biçiminde bir lambda ifadesi döndürmesi gerekir `Expression<Func<T,bool>>` .</span><span class="sxs-lookup"><span data-stu-id="3d5db-125">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="3d5db-126">**[Changeyakalayıcısı (** *entitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="3d5db-126">**[ChangeInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="3d5db-127"><xref:System.Data.Services.ChangeInterceptorAttribute>Hedeflenen varlık kümesi kaynağı IÇIN http get isteği dışında BIR http isteği alındığında, özniteliği uygulanmış metotlar çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3d5db-127">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="3d5db-128">Bu yöntemlerin her zaman dönmesi gerekir `void` ( `Nothing` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3d5db-128">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="3d5db-129">Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti Iletilerini kesme](how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="3d5db-129">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d5db-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d5db-130">See also</span></span>

- [<span data-ttu-id="3d5db-131">Hizmet İşlemleri</span><span class="sxs-lookup"><span data-stu-id="3d5db-131">Service Operations</span></span>](service-operations-wcf-data-services.md)
