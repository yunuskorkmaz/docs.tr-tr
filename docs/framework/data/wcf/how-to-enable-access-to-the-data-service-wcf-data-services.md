---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: veri hizmetine erişimi etkinleştirme (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: veri hizmetine erişimi etkinleştirme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 42be9c4c31da7bbbfef07958deef685d52df597b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765431"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="e978a-103">Nasıl yapılır: veri hizmetine erişimi etkinleştirme (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="e978a-103">How to: Enable Access to the Data Service (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="e978a-104">WCF Veri Hizmetleri, bir veri hizmeti tarafından açığa çıkarılan kaynaklara açıkça erişim vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e978a-104">In WCF Data Services, you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="e978a-105">Bu, yeni bir veri hizmeti oluşturduktan sonra tek tek kaynaklara varlık kümesi olarak açıkça erişim sağlamanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e978a-105">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="e978a-106">Bu konuda, [hızlı](quickstart-wcf-data-services.md)başlangıcı tamamladığınızda oluşturulan Northwind veri hizmetindeki varlık kümelerinin beş bölümüne okuma ve yazma erişiminin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e978a-106">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="e978a-107"><xref:System.Data.Services.EntitySetRights>Numaralandırması kullanılarak tanımlandığından <xref:System.FlagsAttribute> , tek bir varlık kümesi için birden çok izin belirtmek üzere BIR mantıksal or işleci kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e978a-107">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e978a-108">ASP.NET uygulamasına erişebilen tüm istemciler de veri hizmeti tarafından sunulan kaynaklara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="e978a-108">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="e978a-109">Bir üretim verileri hizmetinde, kaynaklara yetkisiz erişimi engellemek için uygulamanın kendisini de güvenli hale getirin.</span><span class="sxs-lookup"><span data-stu-id="e978a-109">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="e978a-110">Daha fazla bilgi için bkz. [ASP.NET Web Sites 'ın güvenliğini sağlama](/previous-versions/aspnet/91f66yxt(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e978a-110">For more information, see [Securing ASP.NET Web Sites](/previous-versions/aspnet/91f66yxt(v=vs.100)).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="e978a-111">Veri hizmetine erişimi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e978a-111">To enable access to the data service</span></span>  
  
- <span data-ttu-id="e978a-112">Veri Hizmeti kodunda, işlevdeki yer tutucu kodunu aşağıdaki gibi değiştirin `InitializeService` :</span><span class="sxs-lookup"><span data-stu-id="e978a-112">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="e978a-113">Bu, istemcilerin ve varlık kümelerine okuma ve yazma erişimi olmasını `Orders` `Order_Details` ve varlık kümelerine salt okuma erişimini sağlar `Customers` .</span><span class="sxs-lookup"><span data-stu-id="e978a-113">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e978a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e978a-114">See also</span></span>

- [<span data-ttu-id="e978a-115">Nasıl yapılır: IIS üzerinde çalışan bir WCF Veri Hizmeti Geliştirme</span><span class="sxs-lookup"><span data-stu-id="e978a-115">How to: Develop a WCF Data Service Running on IIS</span></span>](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [<span data-ttu-id="e978a-116">Veri Hizmeti Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e978a-116">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
