---
title: WCF Veri Hizmetleri İstemci Kitaplığı
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 556482e3e43460016162dfbdd9b31f9a68c0af46
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900885"
---
# <a name="wcf-data-services-client-library"></a>WCF Veri Hizmetleri İstemci Kitaplığı
Bir HTTP isteği gönderebileceği ve bir veri hizmetinin döndürdüğü OData akışını işlebiliyorsanız, herhangi bir uygulama açık veri Protokolü (OData) tabanlı bir veri hizmeti ile etkileşime geçebilir. Bu birlikte çalışabilirlik, çok çeşitli web özellikli uygulamalardan OData tabanlı hizmetlere erişmenizi sağlar. WCF Veri Hizmetleri, .NET Framework veya Silverlight tabanlı uygulamalardan OData akışlarını kullanırken daha zengin bir programlama deneyimi sağlayan istemci kitaplıklarını içerir.  
  
 İstemci kitaplığının iki ana sınıfı <xref:System.Data.Services.Client.DataServiceContext> sınıfıdır ve <xref:System.Data.Services.Client.DataServiceQuery%601> sınıfıdır. <xref:System.Data.Services.Client.DataServiceContext> sınıfı, belirtilen bir veri hizmetine göre desteklenen işlemleri kapsüller. OData Hizmetleri durum bilgisiz olmasına karşın bağlam değildir. Bu nedenle, değişiklik yönetimi gibi özellikleri desteklemek için veri hizmeti ile etkileşimler arasında istemcideki durumu korumak için <xref:System.Data.Services.Client.DataServiceContext> sınıfını kullanabilirsiniz. Bu sınıf Ayrıca kimlikleri yönetir ve değişiklikleri izler. <xref:System.Data.Services.Client.DataServiceQuery%601> sınıfı, belirli bir varlık kümesine karşı bir sorguyu temsil eder.  
  
 Bu bölümde, istemci kitaplıklarının bir .NET Framework istemci uygulamasına erişmek ve verileri değiştirmek için nasıl kullanılacağı açıklanmaktadır. WCF Veri Hizmetleri istemci kitaplığını Silverlight tabanlı bir uygulamayla kullanma hakkında daha fazla bilgi için, bkz. [WCF veri Hizmetleri (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v%3dvs.95)). Diğer istemci kitaplıkları, bir OData akışını diğer türlerde uygulamalarda kullanmanıza olanak sağlayan kullanılabilir. OData SDK hakkında daha fazla bilgi için bkz. [OData SDK-örnek kodu](https://www.odata.org/ecosystem/#sdk).
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Veri Hizmeti İstemci Kitaplığı Oluşturma](generating-the-data-service-client-library-wcf-data-services.md)  
 OData akışlarını temel alan istemci kitaplığı ve istemci veri hizmeti sınıflarının nasıl oluşturulacağını açıklar.  
  
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
 Denetimlerin bir veri hizmeti tarafından döndürülen bir OData akışına nasıl bağlanacağını açıklar.  
  
 [Hizmet İşlemleri Çağırma](calling-service-operations-wcf-data-services.md)  
 Hizmet işlemlerini çağırmak için istemci kitaplığının nasıl kullanılacağını açıklar.  
  
 [Veri Hizmeti Bağlamını Yönetme](managing-the-data-service-context-wcf-data-services.md)  
 İstemci kitaplığı davranışlarını yönetme seçeneklerini açıklar.  
  
 [İkili Verilerle Çalışma](working-with-binary-data-wcf-data-services.md)  
 Veri hizmeti tarafından veri akışı olarak döndürülen ikili verilerin nasıl erişebileceğini ve değiştirileceği açıklanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [Başlarken](getting-started-with-wcf-data-services.md)
