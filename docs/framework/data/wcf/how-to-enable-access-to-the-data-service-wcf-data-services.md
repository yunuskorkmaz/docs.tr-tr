---
title: 'Nasıl yapılır: Veri hizmetini (WCF Veri Hizmetleri) erişimi etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 44f3709cf0a1485c772940e7460d3436a52aa3eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163663"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Nasıl yapılır: Veri hizmetini (WCF Veri Hizmetleri) erişimi etkinleştirme
İçinde [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], açıkça bir veri hizmeti tarafından sunulan kaynakları erişimi vermeniz gerekir. Başka bir deyişle, yeni bir veri hizmeti oluşturduğunuzda, varlık kümelerini olarak tek tek kaynaklarına erişimi hala açıkça sağlamalısınız. Bu konuda okuma etkinleştirme gösterir ve beş varlık yazma erişimi ayarlar tamamladığınızda oluşturduğunuz Northwind veri hizmetinde [hızlı](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Çünkü <xref:System.Data.Services.EntitySetRights> numaralandırması kullanarak tanımlanmıştır <xref:System.FlagsAttribute>küme tek bir varlık için birden fazla izinleri belirtmek için işleci veya bir mantıksal kullanabilirsiniz.  
  
> [!NOTE]
>  ASP.NET uygulamaya erişebilmesi için herhangi bir istemci veri hizmeti tarafından kullanıma sunulan kaynakları da erişebilirsiniz. Bir üretim veri hizmeti kaynaklarına, yetkisiz erişimi önlemek için Ayrıca uygulama güvenli hale getirmelisiniz. Daha fazla bilgi için [ASP.NET Web sitesini güvenli hale getirme](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
### <a name="to-enable-access-to-the-data-service"></a>Veri hizmetine erişiminizi etkinleştirmek için  
  
-   Veri Hizmeti için kodda yer tutucusunu değiştirin `InitializeService` işlevi aşağıdaki:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     Bu istemcilerin okuma ve yazma erişimi sağlar `Orders` ve `Order_Details` varlık setleri ve yalnızca okuma erişimi `Customers` varlık kümesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: IIS üzerinde çalışan bir WCF Veri Hizmeti Geliştirme](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)
- [Veri Hizmeti Yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
