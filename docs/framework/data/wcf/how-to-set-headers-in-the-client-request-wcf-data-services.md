---
title: 'Nasıl yapılır: Istemci Isteğinde üst bilgileri ayarlama (WCF Veri Hizmetleri)'
description: WCF Veri Hizmetleri ' de veri hizmetine gönderilmeden önce istek iletisine yeni bir üst bilgi eklemek için SendingRequest olayını nasıl işleyeceğinizi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 47e40f416b256fbd06160a5ee2683eb8364d48b7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204392"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Nasıl yapılır: Istemci Isteğinde üst bilgileri ayarlama (WCF Veri Hizmetleri)

Açık Veri Protokolü 'Nü (OData) destekleyen bir veri hizmetine erişmek için WCF Veri Hizmetleri istemci kitaplığını kullandığınızda, istemci kitaplığı, veri hizmetine gönderilen istek iletilerinde gerekli HTTP üstbilgilerini otomatik olarak ayarlar. Ancak, istemci kitaplığı, veri hizmeti talep tabanlı kimlik doğrulaması veya tanımlama bilgileri gerektirdiğinde olduğu gibi belirli durumlarda gerekli olan ileti üst bilgilerini ayarlamayı bilmez. Daha fazla bilgi için bkz. [güvenliği WCF veri Hizmetleri](securing-wcf-data-services.md#clientAuthentication). Bu durumlarda, istek iletisindeki ileti üstbilgilerini, gönderilmeden önce el ile ayarlamanız gerekir. Bu konudaki örnekte, <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> veri hizmetine gönderilmeden önce istek iletisine yeni bir üst bilgi eklemek için olayının nasıl işleneceği gösterilmektedir.  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur. OData web sitesinde yayımlanan [Northwind örnek veri hizmetini](https://services.odata.org/Northwind/Northwind.svc/) de kullanabilirsiniz; Bu örnek veri hizmeti salt okunurdur ve değişiklikler kaydedilmeye çalışıldığında bir hata döndürülür. OData web sitesindeki örnek veri hizmetleri anonim kimlik doğrulamasına izin verir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, olay için bir işleyici kaydeder <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> ve sonra veri hizmetinde bir sorgu yürütür.  
  
> [!NOTE]
> Bir veri hizmeti her istek için ileti üstbilgisini el ile ayarlamanızı gerektirdiğinde, <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> `OnContextCreated` Bu örnekte olduğu gibi, veri hizmetini temsil eden varlık kapsayıcısındaki kısmi yöntemi geçersiz kılarak olay işleyicisini kaydetmeyi göz önünde bulundurun `NorthwindEntities` .  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Örnek  

 Aşağıdaki yöntem, olayı işler <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> ve isteğe bir kimlik doğrulama üst bilgisi ekler.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerinin Güvenliğini Sağlama](securing-wcf-data-services.md)
- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
