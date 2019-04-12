---
title: 'Nasıl yapılır: (WCF Veri Hizmetleri) istemci isteğinde üst bilgileri Ayarla'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: bbf306b31dd2bc9cfcfb877351205970fc63706f
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517895"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Nasıl yapılır: (WCF Veri Hizmetleri) istemci isteğinde üst bilgileri Ayarla
Kullanırken [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] destekleyen bir veri hizmetine erişmek için İstemci Kitaplığı [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], istemci kitaplığının veri hizmetine gönderilen istek iletilerinin gerekli HTTP üst bilgilerini otomatik olarak ayarlar. Ancak, veri hizmeti talep tabanlı kimlik doğrulaması veya tanımlama bilgileri gerektirdiğinde gibi bazı durumlarda, gerekli ileti üstbilgileri ayarlamak için istemci kitaplığı bilmez. Daha fazla bilgi için [WCF Veri Hizmetleri güvenli hale getirme](../../../../docs/framework/data/wcf/securing-wcf-data-services.md#clientAuthentication). Gönderilmeden önce bu gibi durumlarda el ile ileti üstbilgileri istek iletisinde ayarlamanız gerekir. Bu konudaki örnek nasıl işleneceğini gösterir <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> veri hizmetine gönderilmeden önce yeni bir üst bilgisi için istek iletisi eklemek için olay.  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Ayrıca [Northwind örnek veri hizmeti](https://go.microsoft.com/fwlink/?LinkId=187426) üzerinde yayımlanan [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web sitesi; bu örnek verileri hizmeti salt okunur ve değişiklikleri farklı kaydedilmeye çalışılırken bir hata döndürür. Örnek verileri hizmetlerine [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web sitesine izin ver, anonim kimlik doğrulaması.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek için bir işleyici kaydeder <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> olay ve sonra veri hizmetine yönelik bir sorgu yürütür.  
  
> [!NOTE]
>  Bir veri hizmeti el ile her istek için ileti üst bilgisini ayarlamak gerektirdiğinde işleyicisi kaydediliyor göz önünde bulundurun <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> kılarak olay `OnContextCreated` kısmi yönteminde verileri temsil eden varlık kapsayıcı hizmeti, hangi Bu durumda `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki yöntem tutamaçları <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> olay ve istek için bir kimlik doğrulama üst bilgisi ekler.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerinin Güvenliğini Sağlama](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)
- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
