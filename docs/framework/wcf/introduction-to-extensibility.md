---
title: Genişletilebilirlik Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
ms.openlocfilehash: ae820e88a790aeaad7c57cde2db84b8168f273a9
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321061"
---
# <a name="introduction-to-extensibility"></a>Genişletilebilirlik Genel Bakış
Windows Communication Foundation (WCF) uygulama modeli, Dağıtılmış uygulamaların iletişim gereksinimlerinin daha büyük bir kısmını çözümlemek için tasarlanmıştır. Ancak varsayılan uygulama modeli ve sistem tarafından belirtilen uygulamaların desteklemediği senaryolar her zaman vardır. WCF genişletilebilirlik modeli, tüm uygulama modelini değiştirme noktasına bile, her düzeyde sistem davranışını değiştirmenize olanak tanıyarak özel senaryoları desteklemeye yöneliktir. Bu konu başlığı altında çeşitli uzantı özetlenmektedir ve her biri hakkında daha fazla bilgi verilmektedir.  
  
## <a name="areas-to-extend"></a>Genişletilecek bölgeler  
 Şunları genişletebilirsiniz:  
  
- Uygulama çalışma zamanı. Bu, uygulama için ileti gönderme ve işlemeyi genişletir. Bu alan ayrıca güvenlik sisteminin, meta veri sisteminin, serileştirme sisteminin ve uygulamayı temel alınan kanal sistemiyle bağlayan bağlamaların ve bağlama öğelerinin genişlemesine de dahildir.  
  
- Kanal ve kanal çalışma zamanı. Bu, ileti düzeyindeki işlevleri, protokol, taşıma ve kodlama desteği sağlayan sistemi genişletir.  
  
- Konak çalışma zamanı. Bu, barındırma uygulama etki alanının ilişkisini kanal ve uygulama çalışma zamanına genişletir.  
  
### <a name="extending-the-application-runtime"></a>Uygulama çalışma zamanını genişletme  
 WCF uygulamalarında, ilgili bir kanala ve uygulamanın kendisi için hedeflenen iletilere yönelik iletiler arasında bir ayrım vardır. Kanal iletileri, güvenli konuşma oluşturma veya güvenilir bir oturum oluşturma gibi kanalla ilgili bazı işlevleri destekler. Bu iletiler, uygulama çalışma zamanı için kullanılamaz; uygulama katmanı dahil etmeden önce bunlar işlenir.  
  
 Uygulama iletileri siz veya müşterinizin oluşturduğu bir istemci veya hizmet işlemini hedefleyen verileri içerir. Bu iletiler, gereksinimlerinize bağlı olarak ileti veya nesne formundaki uygulama düzeyi uzantı sisteminde kullanılabilir.  
  
 Tüm iletiler kanal sisteminden geçer; yalnızca uygulama iletileri kanal sisteminden uygulamaya geçirilir. Yeni kanal düzeyi işlevsellik oluşturmak için Kanal sistemini genişletmelidir. Yeni uygulama düzeyi işlevsellik oluşturmak için, hizmet veya istemci çalışma zamanını (sırasıyla dispatchers ve kanal fabrikaları) genişletmelidir. Uygulama çalışma zamanını genişletme hakkında daha fazla bilgi için bkz. [ServiceHost ve hizmet modeli katmanını genişletme](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
#### <a name="extending-security"></a>Güvenliği Genişletme  
 Belirteçler ve kimlik bilgileri gibi özel güvenlik mekanizmaları oluşturmak için güvenlik sistemini genişletmeniz gerekir. Daha fazla bilgi için bkz. [güvenliği genişletme](./extending/extending-security.md).  
  
#### <a name="extending-metadata"></a>Meta verileri genişletme  
 Meta verilerinizi varsayılandan farklı bir şekilde kullanıma sunmak için meta veri sistemini genişletmelisiniz. Daha fazla bilgi için bkz. [meta veri sistemini genişletme](./extending/extending-the-metadata-system.md).  
  
#### <a name="extending-serialization"></a>Serileştirme genişletme  
 Özel kodlayıcılar oluşturmak, veri yedekleri veya aktarılan verilerin özelleştirmesiyle ilgili diğer işleri sağlamak için serileştirme sistemini genişletmeniz gerekir. Daha fazla bilgi için bkz. [Encoders ve serileştiriciler genişletme](./extending/extending-encoders-and-serializers.md).  
  
#### <a name="extending-bindings"></a>Bağlamaları Genişletme  
 Taşıma veya protokol kanallarını uygulama katmanıyla ilişkilendirmek için, bağlama sistemini genişletmelisiniz. Daha fazla bilgi için bkz. [bağlamaları genişletme](./extending/extending-bindings.md).  
  
### <a name="extending-the-channel-system"></a>Kanal sistemini genişletme  
 Özel aktarımları veya protokol işlevselliğini destekleyen kanallar oluşturmak için bkz. [Kanal Katmanını Genişletme](./extending/extending-the-channel-layer.md).  
  
### <a name="extending-the-service-hosting-system"></a>Hizmet barındırma sistemini genişletme  
 Hizmet genelindeki uygulama modelini değiştirmek için <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> sınıfını genişletmelidir. Daha fazla bilgi için bkz. [ServiceHost ve hizmet modeli katmanını genişletme](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Barındırma uygulaması etki alanı ve hizmet ana bilgisayarı arasındaki ilişkiyi değiştirmek için <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> sınıfını genişletmeniz gerekir. Daha fazla bilgi için bkz. [ServiceHostFactory kullanarak barındırma genişletme](./extending/extending-hosting-using-servicehostfactory.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF'yi Genişletme](./extending/index.md)
