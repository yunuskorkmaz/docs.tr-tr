---
title: WCF Veri Hizmetleri İstemci Kitaplığı
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 9af19f2ef552c5871d488c968368a9192bae9edb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656225"
---
# <a name="wcf-data-services-client-library"></a>WCF Veri Hizmetleri İstemci Kitaplığı
Herhangi bir uygulama ile etkileşim kurabilir bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]-bir HTTP isteği ve işlem gönderirseniz, veri hizmeti tabanlı [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış, bir veri hizmeti döndürür. Bu bir birlikte çalışabilirlik erişmenizi sağlayan [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-tabanlı bir çok çeşitli Web özellikli uygulamalardan hizmetler. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kullandığınız zaman, daha zengin bir programlama deneyimi sağlayan istemci kütüphaneleri içerir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] .NET Framework veya Silverlight tabanlı uygulamalardan akışları.  
  
 İstemci Kitaplığı'nın iki ana sınıflardır <xref:System.Data.Services.Client.DataServiceContext> sınıfı ve <xref:System.Data.Services.Client.DataServiceQuery%601> sınıfı. <xref:System.Data.Services.Client.DataServiceContext> Sınıfı belirtilen veri hizmeti karşı desteklenen işlemler kapsüller. Ancak [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Hizmetleri durum bilgisiz, içeriği değil. Bu nedenle, kullanabileceğiniz <xref:System.Data.Services.Client.DataServiceContext> değişiklik yönetimi gibi özellikleri desteklemek için veri hizmeti ile etkileşim arasında istemci durumunu korumak üzere sınıfı. Bu sınıf ayrıca kimlikleri yöneten ve değişiklikleri izler. <xref:System.Data.Services.Client.DataServiceQuery%601> Sınıf özel varlık kümesinde bir sorgu temsil eder.  
  
 Bu bölümde, erişim ve bir .NET Framework istemci uygulamasından verileri değiştirmek için istemci kitaplıkları kullanmayı açıklar. Nasıl kullanılacağı hakkında daha fazla bilgi için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Silverlight tabanlı bir uygulama ile istemci Kitaplığı'na bakın [WCF Veri Hizmetleri (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=186016). Diğer istemci kitaplıkları vardır ve kullanmasını sağlayan bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] diğer türde uygulamalar akış. Daha fazla bilgi için [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Veri Hizmeti İstemci Kitaplığı Oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 Bir istemci kitaplığı ve temel alan istemci veri hizmeti sınıfları oluşturma adımları anlatılmaktadır [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları.  
  
 [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 .NET Framework tabanlı bir uygulamadan veri hizmeti istemci kitaplıklarını kullanarak sorgu açıklar.  
  
 [Ertelenmiş İçerik Yükleme](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 İlk sorgu yanıtına dahil edilmeyen ek içerik yükleme işlemini açıklar.  
  
 [Veri Hizmetini Güncelleştirme](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 Oluşturabilir, değiştirebilir ve istemci kitaplıklarını kullanarak varlıkları ve ilişkileri silme işlemini açıklamaktadır.  
  
 [Zaman Uyumsuz İşlemler](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 Zaman uyumsuz olarak bir veri hizmeti ile çalışmak için istemci kitaplıkları tarafından sağlanan özellikleri açıklar.  
  
 [Toplu İşlemler](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 İstemci kitaplıkları kullanarak veri hizmetine tek bir toplu işlemde birden çok istek göndermek nasıl açıklar.  
  
 [Veriyi Denetimlere Bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 Denetimlere bağlayabilirsiniz açıklar bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] veri hizmeti tarafından döndürülen akış.  
  
 [Hizmet İşlemleri Çağırma](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 Hizmet işlemlerini aramak üzere istemci kitaplığını kullanmayı açıklar.  
  
 [Veri Hizmeti Bağlamını Yönetme](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 İstemci Kitaplığı'nın davranışının yönetimi için seçenekleri açıklar.  
  
 [İkili Verilerle Çalışma](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 Erişim ve veri akışı olarak veri hizmeti tarafından döndürülen ikili veri değişim açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
