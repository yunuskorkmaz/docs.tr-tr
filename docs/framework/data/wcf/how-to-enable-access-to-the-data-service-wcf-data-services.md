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
ms.workload: dotnet
ms.openlocfilehash: f481a3a918282bf598277dcd4e1bf29d63edddc1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
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
