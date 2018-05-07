---
title: 'Nasıl yapılır: Veri Hizmeti (WCF Veri Hizmetleri) erişimi etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: e383fd493326b417002818d8cf32dc5251bd9c6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Nasıl yapılır: Veri Hizmeti (WCF Veri Hizmetleri) erişimi etkinleştirme
İçinde [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], açıkça bir veri hizmeti tarafından sunulan kaynaklara erişim vermeniz gerekir. Başka bir deyişle, yeni bir veri hizmeti oluşturduktan sonra varlık kümeleri olarak tek tek kaynaklarına erişimi hala açıkça sağlamalısınız. Bu konuda okuma etkinleştirme gösterir ve beş varlık yazma erişimi ayarlar tamamladığınızda oluşturduğunuz Northwind veri hizmetinde [Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Çünkü <xref:System.Data.Services.EntitySetRights> numaralandırma kullanarak tanımlanmış <xref:System.FlagsAttribute>işleci tek bir varlık için birden çok izinleri belirtmek üzere ayarlayın veya bir mantıksal kullanabilirsiniz.  
  
> [!NOTE]
>  ASP.NET uygulamasına erişmek için herhangi bir istemci, ayrıca veri hizmeti tarafından sunulan kaynaklara erişebilir. Bir üretim verileri Hizmeti'nde kaynaklara, yetkisiz erişimi önlemek için Ayrıca uygulama güvenliğini sağlamalısınız. Daha fazla bilgi için bkz: [NIB: ASP.NET güvenliği](http://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d).  
  
### <a name="to-enable-access-to-the-data-service"></a>Veri hizmeti erişimi etkinleştirmek için  
  
-   Veri Hizmeti için kodda yer tutucu kodu `InitializeService` aşağıdaki işleviyle:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     Bu istemciler okuma ve yazma erişimi sağlayan `Orders` ve `Order_Details` varlık kümeleri ve salt okunur erişimi `Customers` varlık kümeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: IIS üzerinde çalışan bir WCF Veri Hizmeti Geliştirme](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [Veri Hizmeti Yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
