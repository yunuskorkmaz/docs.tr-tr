---
title: "Nasıl yapılır: Veri Hizmeti (WCF Veri Hizmetleri) erişimi etkinleştirme"
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
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b41de296143d325ba0e1932831d4a3ef1bd7dc80
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="2f6c5-102">Nasıl yapılır: Veri Hizmeti (WCF Veri Hizmetleri) erişimi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="2f6c5-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="2f6c5-103">İçinde [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], açıkça bir veri hizmeti tarafından sunulan kaynaklara erişim vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f6c5-103">In [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="2f6c5-104">Başka bir deyişle, yeni bir veri hizmeti oluşturduktan sonra varlık kümeleri olarak tek tek kaynaklarına erişimi hala açıkça sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="2f6c5-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="2f6c5-105">Bu konuda okuma etkinleştirme gösterir ve beş varlık yazma erişimi ayarlar tamamladığınızda oluşturduğunuz Northwind veri hizmetinde [Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="2f6c5-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="2f6c5-106">Çünkü <xref:System.Data.Services.EntitySetRights> numaralandırma kullanarak tanımlanmış <xref:System.FlagsAttribute>işleci tek bir varlık için birden çok izinleri belirtmek üzere ayarlayın veya bir mantıksal kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f6c5-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f6c5-107">ASP.NET uygulamasına erişmek için herhangi bir istemci, ayrıca veri hizmeti tarafından sunulan kaynaklara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="2f6c5-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="2f6c5-108">Bir üretim verileri Hizmeti'nde kaynaklara, yetkisiz erişimi önlemek için Ayrıca uygulama güvenliğini sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="2f6c5-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="2f6c5-109">Daha fazla bilgi için bkz: [NIB: ASP.NET güvenliği](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span><span class="sxs-lookup"><span data-stu-id="2f6c5-109">For more information, see [NIB: ASP.NET Security](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="2f6c5-110">Veri hizmeti erişimi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2f6c5-110">To enable access to the data service</span></span>  
  
-   <span data-ttu-id="2f6c5-111">Veri Hizmeti için kodda yer tutucu kodu `InitializeService` aşağıdaki işleviyle:</span><span class="sxs-lookup"><span data-stu-id="2f6c5-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="2f6c5-112">Bu istemciler okuma ve yazma erişimi sağlayan `Orders` ve `Order_Details` varlık kümeleri ve salt okunur erişimi `Customers` varlık kümeleri.</span><span class="sxs-lookup"><span data-stu-id="2f6c5-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f6c5-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2f6c5-113">See Also</span></span>  
 [<span data-ttu-id="2f6c5-114">Nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme</span><span class="sxs-lookup"><span data-stu-id="2f6c5-114">How to: Develop a WCF Data Service Running on IIS</span></span>](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [<span data-ttu-id="2f6c5-115">Veri Hizmeti yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2f6c5-115">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
