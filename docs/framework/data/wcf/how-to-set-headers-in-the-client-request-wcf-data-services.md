---
title: 'Nasıl yapılır: istemci isteği (WCF Veri Hizmetleri) üstbilgilerini Ayarla'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: e6b9b01f18e8412857a38a8e22fadfa88faf9d24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361792"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Nasıl yapılır: istemci isteği (WCF Veri Hizmetleri) üstbilgilerini Ayarla
Kullandığınızda [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] destekleyen bir veri hizmete erişmek için İstemci Kitaplığı [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], istemci kitaplığı veri hizmete gönderilen istek iletilerinin gerekli HTTP üstbilgileri otomatik olarak ayarlar. Ancak, istemci kitaplığının ne zaman veri hizmeti talep tabanlı kimlik doğrulaması veya tanımlama bilgilerini gerektiren belirli durumlarda gereklidir ileti üstbilgilerini Ayarla bilmez. Daha fazla bilgi için bkz: [WCF Veri Hizmetleri güvenli hale getirme](../../../../docs/framework/data/wcf/securing-wcf-data-services.md#clientAuthentication). Gönderilmeden önce bu gibi durumlarda, el ile ileti üstbilgilerini istek iletisinde ayarlamanız gerekir. Bu konudaki örnek nasıl işleneceğini gösterir <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> veri hizmetine gönderilmeden önce yeni bir üstbilgi istek iletisi eklenecek olay.  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Aynı zamanda [Northwind örnek veri hizmeti](http://go.microsoft.com/fwlink/?LinkId=187426) üzerinde yayımlanan [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web sitesi; bu örnek veri hizmetidir salt okunur ve değişikliklerinizi kaydetmeye çalışırken bir hata döndürür. Örnek Veri Hizmetleri üzerinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web sitesinin anonim kimlik doğrulaması izin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek için bir işleyici kaydeder <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> olay ve veri hizmeti bir sorgu yürütür.  
  
> [!NOTE]
>  Veri hizmeti el ile her istek için ileti üstbilgisi ayarlamanızı gerektirir, işleyici için kaydetme göz önünde <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> kılarak olay `OnContextCreated` verileri temsil eden varlık kapsayıcısında kısmi yöntemi hizmet, hangi Bu durum `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki yöntemi işleyiciler <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> olay ve bir kimlik doğrulama üst bilgisi isteğe ekler.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetlerinin Güvenliğini Sağlama](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
