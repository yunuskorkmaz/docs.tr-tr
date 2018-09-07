---
title: 'Nasıl yapılır: Veri Hizmeti (WCF Veri Hizmetleri) erişimi etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: eb9d7cd8e62a73f49fd2b0f2fc2572b01109553b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44070556"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="c826d-102">Nasıl yapılır: Veri Hizmeti (WCF Veri Hizmetleri) erişimi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="c826d-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="c826d-103">İçinde [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], açıkça bir veri hizmeti tarafından sunulan kaynakları erişimi vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c826d-103">In [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="c826d-104">Başka bir deyişle, yeni bir veri hizmeti oluşturduğunuzda, varlık kümelerini olarak tek tek kaynaklarına erişimi hala açıkça sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="c826d-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="c826d-105">Bu konuda okuma etkinleştirme gösterir ve beş varlık yazma erişimi ayarlar tamamladığınızda oluşturduğunuz Northwind veri hizmetinde [hızlı](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="c826d-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="c826d-106">Çünkü <xref:System.Data.Services.EntitySetRights> numaralandırması kullanarak tanımlanmıştır <xref:System.FlagsAttribute>küme tek bir varlık için birden fazla izinleri belirtmek için işleci veya bir mantıksal kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c826d-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c826d-107">ASP.NET uygulamaya erişebilmesi için herhangi bir istemci veri hizmeti tarafından kullanıma sunulan kaynakları da erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c826d-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="c826d-108">Bir üretim veri hizmeti kaynaklarına, yetkisiz erişimi önlemek için Ayrıca uygulama güvenli hale getirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c826d-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="c826d-109">Daha fazla bilgi için [NIB: ASP.NET güvenlik](https://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span><span class="sxs-lookup"><span data-stu-id="c826d-109">For more information, see [NIB: ASP.NET Security](https://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="c826d-110">Veri hizmetine erişiminizi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="c826d-110">To enable access to the data service</span></span>  
  
-   <span data-ttu-id="c826d-111">Veri Hizmeti için kodda yer tutucusunu değiştirin `InitializeService` işlevi aşağıdaki:</span><span class="sxs-lookup"><span data-stu-id="c826d-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="c826d-112">Bu istemcilerin okuma ve yazma erişimi sağlar `Orders` ve `Order_Details` varlık setleri ve yalnızca okuma erişimi `Customers` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="c826d-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c826d-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c826d-113">See Also</span></span>  
 [<span data-ttu-id="c826d-114">Nasıl yapılır: IIS üzerinde çalışan bir WCF Veri Hizmeti Geliştirme</span><span class="sxs-lookup"><span data-stu-id="c826d-114">How to: Develop a WCF Data Service Running on IIS</span></span>](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [<span data-ttu-id="c826d-115">Veri Hizmeti Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c826d-115">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
