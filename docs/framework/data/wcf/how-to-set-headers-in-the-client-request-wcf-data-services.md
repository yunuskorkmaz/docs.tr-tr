---
title: 'Nasıl yapılır: Istemci Isteğinde üst bilgileri ayarlama (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: af158fa525f1f83c081ab293bfdbfb4177caf5a6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348386"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Nasıl yapılır: Istemci Isteğinde üst bilgileri ayarlama (WCF Veri Hizmetleri)
Açık Veri Protokolü 'Nü (OData) destekleyen bir veri hizmetine erişmek için WCF Veri Hizmetleri istemci kitaplığını kullandığınızda, istemci kitaplığı, veri hizmetine gönderilen istek iletilerinde gerekli HTTP üstbilgilerini otomatik olarak ayarlar. Ancak, istemci kitaplığı, veri hizmeti talep tabanlı kimlik doğrulaması veya tanımlama bilgileri gerektirdiğinde olduğu gibi belirli durumlarda gerekli olan ileti üst bilgilerini ayarlamayı bilmez. Daha fazla bilgi için bkz. [güvenliği WCF veri Hizmetleri](securing-wcf-data-services.md#clientAuthentication). Bu durumlarda, istek iletisindeki ileti üstbilgilerini, gönderilmeden önce el ile ayarlamanız gerekir. Bu konudaki örnekte, veri hizmetine gönderilmeden önce istek iletisine yeni bir üst bilgi eklemek için <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> olayının nasıl işleneceği gösterilmektedir.  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur. OData web sitesinde yayımlanan [Northwind örnek veri hizmetini](https://services.odata.org/Northwind/Northwind.svc/) de kullanabilirsiniz; Bu örnek veri hizmeti salt okunurdur ve değişiklikler kaydedilmeye çalışıldığında bir hata döndürülür. OData web sitesindeki örnek veri hizmetleri anonim kimlik doğrulamasına izin verir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> olayı için bir işleyici kaydeder ve sonra veri hizmetinde bir sorgu yürütür.  
  
> [!NOTE]
> Bir veri hizmeti her istek için ileti üstbilgisini el ile ayarlamanızı gerektirdiğinde, bu örnekte `NorthwindEntities`olan veri hizmetini temsil eden varlık kapsayıcısında `OnContextCreated` kısmi yöntemini geçersiz kılarak <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> olayı işleyicisini kaydetmeyi göz önünde bulundurun.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki yöntem <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> olayını işler ve isteğe bir kimlik doğrulama üst bilgisi ekler.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerinin Güvenliğini Sağlama](securing-wcf-data-services.md)
- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
