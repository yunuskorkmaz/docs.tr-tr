---
title: 'Nasıl yapılır: Veri hizmetine erişimi etkinleştir (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: cbe25dcb62adf82921b24623cc4930c3076dd1fa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790669"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="c5044-102">Nasıl yapılır: Veri hizmetine erişimi etkinleştir (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="c5044-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="c5044-103">' [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]De, bir veri hizmeti tarafından açığa çıkarılan kaynaklara açıkça erişim vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5044-103">In [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="c5044-104">Bu, yeni bir veri hizmeti oluşturduktan sonra tek tek kaynaklara varlık kümesi olarak açıkça erişim sağlamanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c5044-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="c5044-105">Bu konuda, [hızlı](quickstart-wcf-data-services.md)başlangıcı tamamladığınızda oluşturulan Northwind veri hizmetindeki varlık kümelerinin beş bölümüne okuma ve yazma erişiminin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c5044-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="c5044-106"><xref:System.Data.Services.EntitySetRights> Numaralandırması kullanılaraktanımlandığından,tekbirvarlıkkümesiiçinbirdençokizinbelirtmeküzerebir<xref:System.FlagsAttribute>mantıksal or işleci kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5044-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5044-107">ASP.NET uygulamasına erişebilen tüm istemciler de veri hizmeti tarafından sunulan kaynaklara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="c5044-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="c5044-108">Bir üretim verileri hizmetinde, kaynaklara yetkisiz erişimi engellemek için uygulamanın kendisini de güvenli hale getirin.</span><span class="sxs-lookup"><span data-stu-id="c5044-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="c5044-109">Daha fazla bilgi için bkz. [ASP.NET Web Sites 'ın güvenliğini sağlama](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c5044-109">For more information, see [Securing ASP.NET Web Sites](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="c5044-110">Veri hizmetine erişimi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="c5044-110">To enable access to the data service</span></span>  
  
- <span data-ttu-id="c5044-111">Veri Hizmeti kodunda, `InitializeService` işlevdeki yer tutucu kodunu aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c5044-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="c5044-112">Bu, `Orders` istemcilerin ve `Order_Details` varlık kümelerine okuma ve yazma erişimi olmasını ve `Customers` varlık kümelerine salt okuma erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5044-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5044-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5044-113">See also</span></span>

- [<span data-ttu-id="c5044-114">Nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme</span><span class="sxs-lookup"><span data-stu-id="c5044-114">How to: Develop a WCF Data Service Running on IIS</span></span>](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [<span data-ttu-id="c5044-115">Veri Hizmeti Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c5044-115">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
