---
title: Geliştirme Kanalları
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: 11e7a78282a3c9f7cd221e2ef44bc43c625e447b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286805"
---
# <a name="developing-channels"></a>Geliştirme Kanalları

Windows Communication Foundation (WCF) uygulama katmanıyla birlikte kullanılabilecek bir protokol veya taşıma kanalı geliştirmek için birkaç adım gerekir. Bu konu, bu adımları açıklar ve daha fazla bilgi için sizi belirli konularda yönlendirir. Kanal modelini ve bu konuda bahsedilen çeşitli türleri anlamak için bkz. [Kanal modeline genel bakış](channel-model-overview.md). Tüm aktarım kanalı örneği için bkz. [Transport: UDP](../samples/transport-udp.md).  
  
## <a name="the-channel-development-task-list"></a>Kanal geliştirme Görev Listesi  

 Kullanıcı tanımlı Kanal oluşturma adımları aşağıdaki gibidir. Tüm kanallar şunları içermelidir:  
  
1. Hangi kanal iletisi değişim desenlerinin ( <xref:System.ServiceModel.Channels.IOutputChannel> ,,, <xref:System.ServiceModel.Channels.IInputChannel> <xref:System.ServiceModel.Channels.IDuplexChannel> <xref:System.ServiceModel.Channels.IRequestChannel> , veya) hangisinin <xref:System.ServiceModel.Channels.IReplyChannel> <xref:System.ServiceModel.Channels.IChannelFactory> <xref:System.ServiceModel.Channels.IChannelListener> destekleyeceği ve bu arabirimlerin oturumsuz çeşitlemelerini destekleyip desteklemediğini belirleyin. Ayrıntılar için bkz. [Ileti değişim modelini seçme](choosing-a-message-exchange-pattern.md).  
  
2. İleti değişim modelinizi destekleyen bir kanal fabrikası ve dinleyicisi ( <xref:System.ServiceModel.Channels.IChannelFactory> ve <xref:System.ServiceModel.Channels.IChannelListener> ) oluşturun. Fabrika geliştirme hakkında ayrıntılar için bkz. [istemci: kanal fabrikaları ve kanallar](client-channel-factories-and-channels.md). Dinleyicileri geliştirme hakkında ayrıntılar için bkz. [hizmet: Kanal dinleyicileri ve kanalları](service-channel-listeners-and-channels.md).  
  
3. Ağa özgü özel durumların ya da uygun türetilmiş sınıfına normalleştirildiğinden emin olun <xref:System.TimeoutException?displayProperty=nameWithType> <xref:System.ServiceModel.CommunicationException> . Ayrıntılar için bkz. [özel durumları ve hataları işleme](handling-exceptions-and-faults.md).  
  
4. Uygulama katmanından kullanımı etkinleştirmek için, <xref:System.ServiceModel.Channels.BindingElement> özel kanalı bir kanal yığınına ekleyen bir ekleyin. Daha fazla bilgi için, bkz. [BindingElement oluşturma](creating-a-bindingelement.md).  
  
 Uygulama katmanında daha kapsamlı destek sağlamak için aşağıdaki ek adımlar gereklidir:  
  
1. Yeni bağlama öğesini yapılandırma sistemine göstermek için bağlama öğesi uzantısı bölümü ekleyin. Daha fazla bilgi için bkz. [yapılandırma ve meta veri desteği](configuration-and-metadata-support.md).  
  
2. Diğer uç noktalara iletişim kurmak için meta veri uzantıları ekleyin. Daha fazla bilgi için bkz. [yapılandırma ve meta veri desteği](configuration-and-metadata-support.md).  
  
3. İyi tanımlanmış bir profile göre bağlama öğeleri yığınını önceden yapılandıran bir bağlama ekleyin. Daha fazla bilgi için bkz. [User-Defined bağlamaları oluşturma](creating-user-defined-bindings.md).  
  
4. Yapılandırma sistemine bağlamayı göstermek için bağlama bölümü ve bağlama yapılandırma öğesi ekleyin. Daha fazla bilgi için bkz. [yapılandırma ve meta veri desteği](configuration-and-metadata-support.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlamaları Genişletme](extending-bindings.md)
