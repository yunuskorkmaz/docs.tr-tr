---
title: 'Nasıl yapılır: Veri hizmetini (WCF Veri Hizmetleri) erişimi etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: d1ce582096de63f60c7f2c99925fa39710bedfb3
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091948"
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
- [Nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)
- [Veri Hizmeti Yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
