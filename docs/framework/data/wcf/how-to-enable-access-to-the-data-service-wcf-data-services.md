---
title: 'Nasıl yapılır: veri hizmetine erişimi etkinleştirme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 0ec9c9a730516b22b4eaa215e042e9393c01d752
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569102"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Nasıl yapılır: veri hizmetine erişimi etkinleştirme (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, bir veri hizmeti tarafından açığa çıkarılan kaynaklara açıkça erişim vermeniz gerekir. Bu, yeni bir veri hizmeti oluşturduktan sonra tek tek kaynaklara varlık kümesi olarak açıkça erişim sağlamanız gerektiği anlamına gelir. Bu konuda, [hızlı](quickstart-wcf-data-services.md)başlangıcı tamamladığınızda oluşturulan Northwind veri hizmetindeki varlık kümelerinin beş bölümüne okuma ve yazma erişiminin nasıl etkinleştirileceği gösterilmektedir. <xref:System.Data.Services.EntitySetRights> numaralandırması <xref:System.FlagsAttribute>kullanılarak tanımlandığından, tek bir varlık kümesi için birden çok izin belirtmek üzere bir mantıksal OR işleci kullanabilirsiniz.  
  
> [!NOTE]
> ASP.NET uygulamasına erişebilen tüm istemciler de veri hizmeti tarafından sunulan kaynaklara erişebilir. Bir üretim verileri hizmetinde, kaynaklara yetkisiz erişimi engellemek için uygulamanın kendisini de güvenli hale getirin. Daha fazla bilgi için bkz. [ASP.NET Web Sites 'ın güvenliğini sağlama](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
### <a name="to-enable-access-to-the-data-service"></a>Veri hizmetine erişimi etkinleştirmek için  
  
- Veri Hizmeti kodunda, `InitializeService` işlevindeki yer tutucu kodunu aşağıdaki gibi değiştirin:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     Bu, istemcilerin `Orders` ve `Order_Details` varlık kümelerine okuma ve yazma erişimi olmasını ve `Customers` varlık kümelerine salt okuma erişimi olmasını sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: IIS üzerinde çalışan bir WCF Veri Hizmeti Geliştirme](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [Veri Hizmeti Yapılandırma](configuring-the-data-service-wcf-data-services.md)
