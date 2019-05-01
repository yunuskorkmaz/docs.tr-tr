---
title: 'Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3e78e7cf0c5acde53d7ee23294fd52134414e860
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856545"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler
Bir Windows Communication Foundation (WCF) hizmetiyle kurulan tüm iletişimlerde üzerinden gerçekleşir *uç noktaları* hizmeti. Uç noktaları, istemcilerin bir WCF hizmeti tarafından sunulan işlevlere erişim sağlar.  
  
 Her uç nokta dört özelliklerini oluşur:  
  
- Uç nokta bulunabileceği gösteren bir adres.  
  
- Bir bağlama için bir istemci uç noktasıyla nasıl iletişim kurabilir belirtir.  
  
- Kullanılabilir işlemleri tanımlayan bir sözleşme.  
  
- Yerel uygulama uç nokta ayrıntılarını belirtin davranışları kümesi.  
  
 Bu konu, bu uç nokta yapısını açıklar ve WCF nesne modelinde nasıl temsil edildiğini açıklar.  
  
## <a name="the-structure-of-an-endpoint"></a>Bir uç nokta yapısı  
 Her uç nokta aşağıdakilerden oluşur:  
  
- Adresi: Adresi benzersiz şekilde uç noktayı tanımlar ve olası söyler, nerede hizmet tüketicileri. WCF nesne modeli tarafından temsil edilir <xref:System.ServiceModel.EndpointAddress> sınıfı. Bir <xref:System.ServiceModel.EndpointAddress> sınıfı içerir:  
  
    - A <xref:System.ServiceModel.EndpointAddress.Uri%2A> hizmetinin adresini temsil eden özellik.  
  
    - Bir <xref:System.ServiceModel.EndpointAddress.Identity%2A> özelliği hizmetin güvenlik kimliğini ve isteğe bağlı ileti üstbilgileri koleksiyonunu temsil eder. İsteğe bağlı ileti üstbilgilerini ek sağlamak için kullanılır ve daha ayrıntılı tanımlamak veya uç nokta ile etkileşime geçmek için adresleme bilgi.  
  
     Daha fazla bilgi için [bir uç nokta adresi belirtme](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
- Bağlama: Bağlama uç noktasıyla iletişim nasıl belirtir. Şunları içerir:  
  
    - (Örneğin, TCP veya HTTP) kullanılacak taşıma protokol.  
  
    - (Örneğin, metin veya ikili) iletileri için kullanılacak kodlama.  
  
    - Gerekli güvenlik gereksinimlerini (örneğin, SSL veya SOAP ileti güvenliği).  
  
     Daha fazla bilgi için [WCF bağlamaları genel bakış](../../../../docs/framework/wcf/bindings-overview.md). Bir bağlama WCF nesne modelinde soyut taban sınıfı tarafından temsil edilen <xref:System.ServiceModel.Channels.Binding>. Çoğu senaryo için kullanıcılara sistem tarafından sağlanan bağlamalar birini kullanabilirsiniz. Daha fazla bilgi için [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
- Sözleşmeler: Sözleşme istemciye uç noktasını kullanıma sunar işlevler açıklanmaktadır. Bir sözleşme belirtir:  
  
    - Hangi işlemleri, bir istemci tarafından çağrılabilir.  
  
    - İleti biçimi.  
  
    - Giriş parametreleri veya çağrı işlemi için gerekli veri türü.  
  
    - Ne tür bir işlem veya yanıt iletisi, istemci bekleyebilirsiniz.  
  
     Bir sözleşme tanımlama hakkında daha fazla bilgi için bkz. [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
- Davranışlar: Uç nokta davranışları, yerel hizmet uç noktası davranışını özelleştirmek için kullanabilirsiniz. Uç nokta davranışları bir WCFruntime oluşturma sürecinde katılarak elde edin. Bir uç nokta davranışı örneğidir <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> özelliği bir SOAP veya Web Hizmetleri Açıklama Dili (WSDL) adresi dinleme adresinizden farklı belirtmenizi sağlar. Daha fazla bilgi için [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).  
  
## <a name="defining-endpoints"></a>Uç noktaları tanımlama  
 Uç nokta ya da kesin kod kullanarak bir hizmet için veya yapılandırma yoluyla bildirimli olarak belirtebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Yapılandırma içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) ve [nasıl yapılır: Kod içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 Bu bölümde bağlamaları, uç noktaları ve adres amacını açıklar; bir bağlama ve bir uç nokta nasıl yapılandırılacağını gösterir. ve nasıl kullanılacağını gösteren `ClientVia` davranışı ve `ListenUri` özelliği.  
  
 [Adresler](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 Uç noktaları WCF'de nasıl ele alınır açıklar.  
  
 [Bağlamalar](../../../../docs/framework/wcf/feature-details/bindings.md)  
 Aktarım, kodlama ve istemciler ve hizmetler birbirleri ile iletişim kurmak için gerekli Protokolü ayrıntıları belirtmek için bağlamaları nasıl kullanıldığını açıklar.  
  
 [Anlaşmalar](../../../../docs/framework/wcf/feature-details/contracts.md)  
 Nasıl yöntemlerini hizmet sözleşmelerini tanımlamak açıklar.  
  
 [Nasıl yapılır: Yapılandırma içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 Yapılandırma içinde hizmet uç noktası oluşturma işlemini açıklamaktadır.  
  
 [Nasıl yapılır: Kod içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 Kod içinde hizmet uç noktası oluşturma işlemini açıklamaktadır.  
  
 [Nasıl yapılır: Derlenmiş hizmet kodunu doğrulamak için svcutil.exe kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 Hizmetini kullanarak barındırma olmadan hizmet uygulamaları ve yapılandırmalarında hataları algılamak nasıl açıklar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Yapılandırma](../../../../docs/framework/wcf/configuring-services.md)
- [Bağlamaları Genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)
