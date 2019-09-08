---
title: WCF Veri Hizmetleri İstemci Kitaplığı
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 545442b0086361c8ce8c0482801afc10b1fee96e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779676"
---
# <a name="wcf-data-services-client-library"></a>WCF Veri Hizmetleri İstemci Kitaplığı
Herhangi bir uygulama, bir http [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]isteği gönderebileceği ve bir veri hizmetinin döndürdüğü [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışı işlebiliyorsanız, tabanlı bir veri hizmetiyle etkileşime geçebilir. Bu birlikte çalışabilirlik, çok çeşitli [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]web özellikli uygulamalardan erişim tabanlı hizmetlere erişmenizi sağlar. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].NET Framework veya Silverlight tabanlı uygulamalardan [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları kullanırken daha zengin bir programlama deneyimi sağlayan istemci kitaplıklarını içerir.  
  
 İstemci kitaplığının <xref:System.Data.Services.Client.DataServiceContext> iki ana sınıfı sınıfı <xref:System.Data.Services.Client.DataServiceQuery%601> ve sınıfıdır. Sınıfı <xref:System.Data.Services.Client.DataServiceContext> , belirtilen bir veri hizmetine göre desteklenen işlemleri kapsüller. Hizmetler [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] durum bilgisiz olsa da bağlam değildir. Bu nedenle, değişiklik yönetimi gibi <xref:System.Data.Services.Client.DataServiceContext> özellikleri desteklemek için veri hizmeti ile etkileşimler arasında istemcideki durumu korumak için sınıfını kullanabilirsiniz. Bu sınıf Ayrıca kimlikleri yönetir ve değişiklikleri izler. Sınıfı <xref:System.Data.Services.Client.DataServiceQuery%601> , belirli bir varlık kümesine karşı bir sorguyu temsil eder.  
  
 Bu bölümde, istemci kitaplıklarının bir .NET Framework istemci uygulamasına erişmek ve verileri değiştirmek için nasıl kullanılacağı açıklanmaktadır. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığını Silverlight tabanlı bir uygulamayla kullanma hakkında daha fazla bilgi için, bkz. [WCF veri Hizmetleri (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=186016). Diğer istemci kitaplıkları, bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışı diğer türlerde uygulamalarda kullanmanıza olanak sağlayan kullanılabilir. Daha fazla bilgi için bkz. [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Veri Hizmeti İstemci Kitaplığı Oluşturma](generating-the-data-service-client-library-wcf-data-services.md)  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Akışlara dayalı istemci kitaplığı ve istemci veri hizmeti sınıflarının nasıl oluşturulacağını açıklar.  
  
 [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)  
 İstemci kitaplıklarını kullanarak bir veri hizmetinin .NET Framework tabanlı bir uygulamadan nasıl sorgulanılacağını açıklar.  
  
 [Ertelenmiş İçerik Yükleme](loading-deferred-content-wcf-data-services.md)  
 İlk sorgu yanıtında bulunmayan ek içeriğin nasıl yükleneceğini açıklar.  
  
 [Veri Hizmetini Güncelleştirme](updating-the-data-service-wcf-data-services.md)  
 İstemci kitaplıklarını kullanarak varlıkları ve ilişkileri oluşturma, değiştirme ve silme işlemlerinin nasıl yapılacağını açıklar.  
  
 [Zaman Uyumsuz İşlemler](asynchronous-operations-wcf-data-services.md)  
 Zaman uyumsuz bir şekilde veri hizmetiyle çalışmak için istemci kitaplıkları tarafından sunulan tesislerin açıklar.  
  
 [Toplu İşlemler](batching-operations-wcf-data-services.md)  
 İstemci kitaplıklarını kullanarak tek bir toplu işte veri hizmetine birden çok isteğin nasıl gönderileceğini açıklar.  
  
 [Veriyi Denetimlere Bağlama](binding-data-to-controls-wcf-data-services.md)  
 Denetimlerin bir veri hizmeti tarafından döndürülen bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışa nasıl bağlanacağını açıklar.  
  
 [Hizmet İşlemleri Çağırma](calling-service-operations-wcf-data-services.md)  
 Hizmet işlemlerini çağırmak için istemci kitaplığının nasıl kullanılacağını açıklar.  
  
 [Veri Hizmeti Bağlamını Yönetme](managing-the-data-service-context-wcf-data-services.md)  
 İstemci kitaplığı davranışlarını yönetme seçeneklerini açıklar.  
  
 [İkili Verilerle Çalışma](working-with-binary-data-wcf-data-services.md)  
 Veri hizmeti tarafından veri akışı olarak döndürülen ikili verilerin nasıl erişebileceğini ve değiştirileceği açıklanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [Başlarken](getting-started-with-wcf-data-services.md)
