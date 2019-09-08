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
ms.openlocfilehash: 7decfdd738e71a01afa8cb32604953142b46e588
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790445"
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="70c77-102">Yakalayıcılar (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="70c77-102">Interceptors (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="70c77-103">bir işleme özel mantık ekleyebilmeniz için, bir uygulamanın istek iletilerini ele almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="70c77-103">enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="70c77-104">Gelen iletilerdeki verileri doğrulamak için bu özel mantığı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70c77-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="70c77-105">Ayrıca, istek başına özel bir yetkilendirme ilkesi eklemek gibi bir sorgu isteğinin kapsamını kısıtlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70c77-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="70c77-106">Yakatasyon, veri hizmetindeki özel olarak öznitelikli yöntemler tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="70c77-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="70c77-107">Bu yöntemler tarafından [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ileti işleme uygun noktada çağrılır.</span><span class="sxs-lookup"><span data-stu-id="70c77-107">These methods are called by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] at the appropriate point in message processing.</span></span> <span data-ttu-id="70c77-108">Yakalayıcılar, varlık başına ayarlanan temelinde tanımlanır ve bakım yöntemleri, hizmet işlemleri gibi istekten parametreleri kabul edemez.</span><span class="sxs-lookup"><span data-stu-id="70c77-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="70c77-109">Bir HTTP GET isteği işlenirken çağrılan sorgu yakalayıcısı yöntemleri, bir yakacının varlık kümesi örneğinin sorgu sonuçları tarafından döndürülüp döndürülmeyeceğini belirleyen bir lambda ifadesi döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="70c77-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="70c77-110">Bu ifade, istenen işlemi daha fazla iyileştirmek için veri hizmeti tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70c77-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="70c77-111">Aşağıda sorgu yakalayıcısı 'nın örnek bir tanımı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="70c77-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="70c77-112">Daha fazla bilgi için [nasıl yapılır: Veri hizmeti Iletilerini](how-to-intercept-data-service-messages-wcf-data-services.md)durdurur.</span><span class="sxs-lookup"><span data-stu-id="70c77-112">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="70c77-113">Sorgu olmayan işlemler işlenirken çağrılan, değişiklik dinleyicileri ( `void` `Nothing` Visual Basic) döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="70c77-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="70c77-114">Değişiklik yakalayıcısı metotları aşağıdaki iki parametreyi kabul etmelidir:</span><span class="sxs-lookup"><span data-stu-id="70c77-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1. <span data-ttu-id="70c77-115">Varlık kümesinin varlık türü ile uyumlu olan bir türün parametresi.</span><span class="sxs-lookup"><span data-stu-id="70c77-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="70c77-116">Veri hizmeti değişiklik yakalayıcısını istediğinde, bu parametrenin değeri istek tarafından gönderilen varlık bilgilerini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="70c77-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2. <span data-ttu-id="70c77-117">Türünde <xref:System.Data.Services.UpdateOperations>bir parametre.</span><span class="sxs-lookup"><span data-stu-id="70c77-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="70c77-118">Veri hizmeti değişiklik yakalayıcısını istediğinde, bu parametrenin değeri isteğin gerçekleştirmeye çalıştığı işlemi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="70c77-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="70c77-119">Aşağıda, değişiklik yakalayıcısı 'nın örnek bir tanımı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="70c77-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="70c77-120">Daha fazla bilgi için [nasıl yapılır: Veri hizmeti Iletilerini](how-to-intercept-data-service-messages-wcf-data-services.md)durdurur.</span><span class="sxs-lookup"><span data-stu-id="70c77-120">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="70c77-121">Aşağıdaki öznitelikler, yakalaşmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="70c77-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="70c77-122">**[Queryyakalayıcısı (** *entitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="70c77-122">**[QueryInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="70c77-123"><xref:System.Data.Services.QueryInterceptorAttribute> Özniteliği uygulanmış olan Yöntemler, hedeflenen varlık kümesi kaynağı için bir http get isteği alındığında çağırılır.</span><span class="sxs-lookup"><span data-stu-id="70c77-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="70c77-124">Bu yöntemlerin, her zaman biçiminde `Expression<Func<T,bool>>`bir lambda ifadesi döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="70c77-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="70c77-125">**[Changeyakalayıcısı (** *entitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="70c77-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="70c77-126">Hedeflenen varlık kümesi kaynağı için http get isteği dışında bir http isteği alındığında, özniteliğiuygulanmışmetotlarçağırılır.<xref:System.Data.Services.ChangeInterceptorAttribute></span><span class="sxs-lookup"><span data-stu-id="70c77-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="70c77-127">Bu yöntemlerin her zaman dönmesi `void` gerekir`Nothing` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="70c77-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="70c77-128">Daha fazla bilgi için [nasıl yapılır: Veri hizmeti Iletilerini](how-to-intercept-data-service-messages-wcf-data-services.md)durdurur.</span><span class="sxs-lookup"><span data-stu-id="70c77-128">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70c77-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70c77-129">See also</span></span>

- [<span data-ttu-id="70c77-130">Hizmet İşlemleri</span><span class="sxs-lookup"><span data-stu-id="70c77-130">Service Operations</span></span>](service-operations-wcf-data-services.md)
