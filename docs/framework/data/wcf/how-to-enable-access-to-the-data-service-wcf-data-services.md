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
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Nasıl yapılır: veri hizmetine erişimi etkinleştirme (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Veri Hizmetleri, bir veri hizmeti tarafından açığa çıkarılan kaynaklara açıkça erişim vermeniz gerekir. Bu, yeni bir veri hizmeti oluşturduktan sonra tek tek kaynaklara varlık kümesi olarak açıkça erişim sağlamanız gerektiği anlamına gelir. Bu konuda, [hızlı](quickstart-wcf-data-services.md)başlangıcı tamamladığınızda oluşturulan Northwind veri hizmetindeki varlık kümelerinin beş bölümüne okuma ve yazma erişiminin nasıl etkinleştirileceği gösterilmektedir. <xref:System.Data.Services.EntitySetRights>Numaralandırması kullanılarak tanımlandığından <xref:System.FlagsAttribute> , tek bir varlık kümesi için birden çok izin belirtmek üzere BIR mantıksal or işleci kullanabilirsiniz.  
  
> [!NOTE]
> ASP.NET uygulamasına erişebilen tüm istemciler de veri hizmeti tarafından sunulan kaynaklara erişebilir. Bir üretim verileri hizmetinde, kaynaklara yetkisiz erişimi engellemek için uygulamanın kendisini de güvenli hale getirin. Daha fazla bilgi için bkz. [ASP.NET Web Sites 'ın güvenliğini sağlama](/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
### <a name="to-enable-access-to-the-data-service"></a>Veri hizmetine erişimi etkinleştirmek için  
  
- Veri Hizmeti kodunda, işlevdeki yer tutucu kodunu aşağıdaki gibi değiştirin `InitializeService` :  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     Bu, istemcilerin ve varlık kümelerine okuma ve yazma erişimi olmasını `Orders` `Order_Details` ve varlık kümelerine salt okuma erişimini sağlar `Customers` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: IIS üzerinde çalışan bir WCF Veri Hizmeti Geliştirme](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [Veri Hizmeti Yapılandırma](configuring-the-data-service-wcf-data-services.md)
