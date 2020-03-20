---
title: 'Nasıl yapılır: İstemci İsteğinde Üstbilgileri Ayarlama (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 9267f0e5b68823516764891a40e1435c1325b77f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174348"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Nasıl yapılır: İstemci İsteğinde Üstbilgileri Ayarlama (WCF Veri Hizmetleri)
Açık Veri Protokolü'nü (OData) destekleyen bir veri hizmetine erişmek için WCF Veri Hizmetleri istemci kitaplığını kullandığınızda, istemci kitaplığı veri hizmetine gönderilen istek iletilerinde gerekli HTTP üstbilgilerini otomatik olarak ayarlar. Ancak, istemci kitaplığı, veri hizmetinin talep tabanlı kimlik doğrulaması veya tanımlama bilgileri gerektirmesi gibi belirli durumlarda gerekli olan ileti üstbilgilerini ayarlamayı bilmez. Daha fazla bilgi için [WCF Veri Hizmetlerinin Güvenliğini Sağlama'ya](securing-wcf-data-services.md#clientAuthentication)bakın. Bu gibi durumlarda, ileti üstbilgilerini gönderilmeden önce istek iletisinde el ile ayarlamanız gerekir. Bu konudaki örnek, veri <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> hizmetine gönderilmeden önce istek iletisine yeni bir üstbilgi eklemek için olayın nasıl işleyeceğini gösterir.  
  
 Bu konudaki örnek, Northwind örnek veri hizmetini ve otomatik olarak oluşturulan istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları [WCF Veri Hizmetleri quickstart](quickstart-wcf-data-services.md)tamamladığınızda oluşturulur. OData Web sitesinde yayınlanan [Northwind örnek veri hizmetini](https://services.odata.org/Northwind/Northwind.svc/) de kullanabilirsiniz; bu örnek veri hizmeti salt okunur ve değişiklikleri kaydetmeye çalışmak bir hata döndürür. OData web sitesindeki örnek veri hizmetleri anonim kimlik doğrulamaya izin verir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek olay için <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> bir işleyici kaydeder ve sonra veri hizmetikarşı bir sorgu yürütür.  
  
> [!NOTE]
> Bir veri hizmeti, her istek için ileti üstbilgisini el ile ayarlamanızı <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> gerektiriyorsa, `OnContextCreated` veri hizmetini temsil eden varlık kapsayıcısındaki kısmi yöntemi `NorthwindEntities`geçersiz kılarak olay için işleyiciyi kaydetmeyi düşünün, bu durumda .  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki yöntem <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> olayı işler ve isteğe kimlik doğrulama üstbilgisi ekler.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerinin Güvenliğini Sağlama](securing-wcf-data-services.md)
- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
