---
title: 'Nasıl yapılır: Istemci Isteğinde üst bilgileri ayarla (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 5a72b349526d5cbba229cba627c23b1b1b889678
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943927"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Nasıl yapılır: Istemci Isteğinde üst bilgileri ayarla (WCF Veri Hizmetleri)
'[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]Yi destekleyen bir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] veri hizmetine erişmek için istemci kitaplığını kullandığınızda, istemci kitaplığı, veri hizmetine gönderilen istek iletilerinde gerekli HTTP üstbilgilerini otomatik olarak ayarlar. Ancak, istemci kitaplığı, veri hizmeti talep tabanlı kimlik doğrulaması veya tanımlama bilgileri gerektirdiğinde olduğu gibi belirli durumlarda gerekli olan ileti üst bilgilerini ayarlamayı bilmez. Daha fazla bilgi için bkz. [güvenliği WCF veri Hizmetleri](../../../../docs/framework/data/wcf/securing-wcf-data-services.md#clientAuthentication). Bu durumlarda, istek iletisindeki ileti üstbilgilerini, gönderilmeden önce el ile ayarlamanız gerekir. Bu konudaki örnekte, veri hizmetine gönderilmeden önce istek iletisine <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> yeni bir üst bilgi eklemek için olayının nasıl işleneceği gösterilmektedir.  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web sitesinde yayımlanan [Northwind örnek veri hizmetini](https://go.microsoft.com/fwlink/?LinkId=187426) de kullanabilirsiniz; Bu örnek veri hizmeti salt okunurdur ve değişiklikler kaydedilmeye çalışıldığında bir hata döndürülür. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web sitesindeki örnek veri hizmetleri anonim kimlik doğrulamasına izin verir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> olay için bir işleyici kaydeder ve sonra veri hizmetinde bir sorgu yürütür.  
  
> [!NOTE]
> Bir veri hizmeti her istek için el ile ileti üstbilgisini ayarlamanızı gerektirdiğinde, veri hizmetini temsil eden varlık kapsayıcısında <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> `OnContextCreated` kısmi yöntemi geçersiz kılarak olay işleyicisini kaydetmeyi göz önünde bulundurun. Bu durum `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki yöntem, <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> olayı işler ve isteğe bir kimlik doğrulama üst bilgisi ekler.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerinin Güvenliğini Sağlama](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)
- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
