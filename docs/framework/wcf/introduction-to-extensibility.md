---
title: Genişletilebilirlik Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
ms.openlocfilehash: 8d7b9c811c557b10160c2581a59f5ebf72882bfd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147049"
---
# <a name="introduction-to-extensibility"></a>Genişletilebilirlik Genel Bakış
Windows Communication Foundation (WCF) uygulama modeli, iletişimi gereksinimleri herhangi bir dağıtılmış uygulamanın büyük kısmını çözmek için tasarlanmıştır. Ancak, sistem tarafından sağlanan uygulamaları ve varsayılan uygulama modelini desteklemeyen senaryoları her zaman vardır. WCF genişletilebilirlik modeli, tüm uygulama modelini değiştirme noktasına bile her düzeyde sistemi davranışını değiştirmek sağlayarak özel senaryoları desteklemek üzere tasarlanmıştır. Bu konu, uzantı çeşitli alanlarına özetler ve her hakkında daha fazla bilgi için işaret eder.  
  
## <a name="areas-to-extend"></a>Genişletmek için alanları  
 Genişletebilirsiniz:  
  
-   Uygulama çalışma zamanı. Bu, dağıtma ve uygulamanın iletilerinin işlenmesini genişletir. Bu alan ayrıca güvenlik sistemi, meta veri sistemini, serileştirme sistem ve bağlamaları genişletme ve bağlama uygulamayı arka plandaki kanal sistemiyle bağlama öğeleri içerir.  
  
-   Kanalı ve kanal çalışma zamanı. Bu protokolü, Aktarım, sağlama ve Destek kodlama ileti düzeyinde işlevleri sistem genişletir.  
  
-   Çalışma zamanı ana bilgisayarı. Bu kanal ve uygulama çalışma zamanı barındırma uygulama etki alanı ilişkisi genişletir.  
  
### <a name="extending-the-application-runtime"></a>Uygulama çalışma zamanı genişletme  
 WCF uygulamaları için karşılık gelen bir kanal gidecek iletiler ve uygulama için hedeflenen iletiler arasında bir ayrım yoktur. Kanal iletileri güvenli konuşma oluşturma veya bir güvenilir oturum oluşturma gibi bazı kanal ile ilgili işlevler destekler. Bu iletiler, uygulama çalışma zamanı için kullanılamaz; uygulama katmanı söz konusu önce işlenir.  
  
 Bir istemci için giden veri veya siz veya müşteriniz oluşturduğu hizmet işlemi uygulama iletileri içerir. Bu iletiler, uygulama düzeyinde uzantı sistemi gereksinimlerinize bağlı olarak, ileti veya nesne formunda kullanılabilir.  
  
 Tüm iletileri kanal sistem üzerinden geçirin; yalnızca uygulama iletileri kanal sistemden uygulamaya geçirilir. Yeni kanal düzeyi işlevi oluşturmak için kanal sistem genişletmeniz gerekir. Yeni uygulama düzeyi işlevi oluşturmak için hizmet veya istemci çalışma zamanı genişletmeniz gerekir (Dağıtıcıları ve kanal fabrikaları sırasıyla). Uygulama çalışma zamanı genişletme hakkında daha fazla bilgi için bkz. [genişletme ServiceHost ve hizmet modeli katmanını](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
#### <a name="extending-security"></a>Güvenliği Genişletme  
 Özel güvenlik mekanizmaları belirteçleri ve kimlik bilgileri gibi oluşturmak için güvenlik sistemi genişletmeniz gerekir. Daha fazla bilgi için [genişletme güvenlik](../../../docs/framework/wcf/extending/extending-security.md).  
  
#### <a name="extending-metadata"></a>Meta verileri genişletme  
 Meta verilerinizi, varsayılandan farklı bir şekilde kullanıma sunmak için meta veri sistemini genişletmeniz gerekir. Daha fazla bilgi için [meta veri sistemini genişletme](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
#### <a name="extending-serialization"></a>Serileştirme genişletme  
 Özel kodlayıcılar yapı, veriler yedeklerin veya özelleştirme aktarılan veriler ile ilgili diğer işleri sağlamak için serileştirme sistem genişletmeniz gerekir. Daha fazla bilgi için [genişletme kodlayıcılar ve seri hale getiricileri genişletme](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).  
  
#### <a name="extending-bindings"></a>Bağlamaları Genişletme  
 Taşıma veya protokol kanalları uygulama katmanı ile ilişkilendirmek için bağlama sistemi genişletmeniz gerekir. Daha fazla bilgi için [bağlamaları genişletme](../../../docs/framework/wcf/extending/extending-bindings.md).  
  
### <a name="extending-the-channel-system"></a>Kanal sistemini genişletme  
 Destek özel taşımalar veya protokol işlevselliği kanallar oluşturmak için bkz [kanal katmanını genişletme](../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
### <a name="extending-the-service-hosting-system"></a>Sistem barındırma hizmeti genişletme  
 Hizmet genelinde uygulama modeli değiştirmek için genişletmelidir <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> sınıfı. Daha fazla bilgi için [genişletme ServiceHost ve hizmet modeli katmanını](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Uygulama etki alanı barındırma ve hizmet ana bilgisayarı arasındaki ilişkiyi değiştirmek için genişletmelidir <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> sınıfı. Daha fazla bilgi için [genişletme barındırma ServiceHostFactory kullanarak](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF'yi Genişletme](../../../docs/framework/wcf/extending/index.md)
