---
title: Dinleyiciler (WCF Veri Hizmetleri)
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
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7aad516b819723c97a40a016a46ddcbe0fcdf4d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="e386e-102">Dinleyiciler (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="e386e-102">Interceptors (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="e386e-103">bir uygulama için bir işlem Özel mantık ekleyebilmeleri istek iletilerini müdahale sağlar.</span><span class="sxs-lookup"><span data-stu-id="e386e-103"> enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="e386e-104">Gelen iletilere verileri doğrulamak için bu özel mantık kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e386e-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="e386e-105">Daha fazla kapsamı bir sorgu isteği gibi bir istek başına temelinde özel yetkilendirme ilkesi eklemek için kısıtlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e386e-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="e386e-106">Kişiler tarafından ele özel öznitelikli yöntemlerinde veri hizmeti tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e386e-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="e386e-107">Bu yöntemleri tarafından çağrılır [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ileti işleme uygun noktasında.</span><span class="sxs-lookup"><span data-stu-id="e386e-107">These methods are called by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] at the appropriate point in message processing.</span></span> <span data-ttu-id="e386e-108">Tek başına varlık kümesi temelinde dinleyiciler tanımlanır ve hizmet işlemleri gibi dinleyiciyi yöntemleri İstek parametreleri kabul edemez.</span><span class="sxs-lookup"><span data-stu-id="e386e-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="e386e-109">Bir HTTP GET isteği işlerken, sorgu dinleyiciyi yöntemleri, sorgu sonuçları tarafından ayarlanan dinleyiciyi'nın varlık örneği olup olmadığını belirleyen bir lambda ifadesi döndürülmelidir döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e386e-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="e386e-110">Bu ifade, istenen işlem daha fazla daraltmak için veri hizmeti tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e386e-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="e386e-111">Aşağıda bir örnek sorgu dinleyiciyi tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="e386e-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="e386e-112">Daha fazla bilgi için bkz: [nasıl yapılır: veri hizmeti iletileri müdahale](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e386e-112">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="e386e-113">Sorgu olmayan işlemleri işlerken olarak adlandırılır, değişiklik dinleyiciler döndürmelidir `void` (`Nothing` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="e386e-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="e386e-114">Değişiklik dinleyiciyi yöntemleri, aşağıdaki iki parametreyi kabul etmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="e386e-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1.  <span data-ttu-id="e386e-115">Varlık kümesinin varlık türüyle uyumlu bir türde bir parametresi.</span><span class="sxs-lookup"><span data-stu-id="e386e-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="e386e-116">Veri Hizmeti değişiklik dinleyiciyi çalıştırdığında, bu parametrenin değeri istek tarafından gönderilen varlık bilgileri yansıtır.</span><span class="sxs-lookup"><span data-stu-id="e386e-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2.  <span data-ttu-id="e386e-117">Türünde bir parametre <xref:System.Data.Services.UpdateOperations>.</span><span class="sxs-lookup"><span data-stu-id="e386e-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="e386e-118">Veri Hizmeti değişiklik dinleyiciyi çalıştırdığında, bu parametrenin değeri isteği gerçekleştirmeye çalışırken işlemi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="e386e-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="e386e-119">Aşağıda bir örnek bir değişiklik dinleyiciyi tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="e386e-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="e386e-120">Daha fazla bilgi için bkz: [nasıl yapılır: veri hizmeti iletileri müdahale](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e386e-120">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="e386e-121">Aşağıdaki öznitelikler kişiler tarafından ele için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e386e-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="e386e-122">**[QueryInterceptor (** *EnitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="e386e-122">**[QueryInterceptor(** *EnitySetName* **)]**</span></span>  
 <span data-ttu-id="e386e-123">Yöntemleriyle <xref:System.Data.Services.QueryInterceptorAttribute> uygulanan öznitelik kaynak hedef varlık kümesi için bir HTTP GET isteği alındığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e386e-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="e386e-124">Bu yöntemlerin her zaman biçiminde bir lambda ifadesi döndürmelidir `Expression<Func<T,bool>>`.</span><span class="sxs-lookup"><span data-stu-id="e386e-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="e386e-125">**[ChangeInterceptor (** *EnitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="e386e-125">**[ChangeInterceptor(** *EnitySetName* **)]**</span></span>  
 <span data-ttu-id="e386e-126">Yöntemleriyle <xref:System.Data.Services.ChangeInterceptorAttribute> uygulanan öznitelik kaynak hedef varlık kümesi için HTTP GET isteği dışında bir HTTP isteği alındığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e386e-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="e386e-127">Bu yöntemlerin her zaman döndürmelidir `void` (`Nothing` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="e386e-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="e386e-128">Daha fazla bilgi için bkz: [nasıl yapılır: veri hizmeti iletileri müdahale](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e386e-128">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e386e-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e386e-129">See Also</span></span>  
 [<span data-ttu-id="e386e-130">Hizmet işlemleri</span><span class="sxs-lookup"><span data-stu-id="e386e-130">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)
