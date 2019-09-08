---
title: Geliştirme Kanalları
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: 8d0ecb9ea473b78dfc648a1087ae2261406f2b4f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795781"
---
# <a name="developing-channels"></a>Geliştirme Kanalları
Windows Communication Foundation (WCF) uygulama katmanıyla birlikte kullanılabilecek bir protokol veya taşıma kanalı geliştirmek için birkaç adım gerekir. Bu konu, bu adımları açıklar ve daha fazla bilgi için sizi belirli konularda yönlendirir. Kanal modelini ve bu konuda bahsedilen çeşitli türleri anlamak için bkz. [Kanal modeline genel bakış](channel-model-overview.md). Tüm aktarım kanalı örneği için bkz [. taşıma: UDP](../samples/transport-udp.md).  
  
## <a name="the-channel-development-task-list"></a>Kanal geliştirme Görev Listesi  
 Kullanıcı tanımlı Kanal oluşturma adımları aşağıdaki gibidir. Tüm kanallar şunları içermelidir:  
  
1. Hangi kanal iletisi değişim<xref:System.ServiceModel.Channels.IOutputChannel>desenlerinin (, <xref:System.ServiceModel.Channels.IInputChannel>, <xref:System.ServiceModel.Channels.IChannelFactory> <xref:System.ServiceModel.Channels.IReplyChannel> <xref:System.ServiceModel.Channels.IDuplexChannel>,, veya) hangisinin destekleyeceği ve <xref:System.ServiceModel.Channels.IChannelListener> oturumlarınızın desteklenip desteketkinleştirilmeyeceğini belirleyin <xref:System.ServiceModel.Channels.IRequestChannel> Bu arabirimlerin çeşitlemeleri. Ayrıntılar için bkz. [Ileti değişim modelini seçme](choosing-a-message-exchange-pattern.md).  
  
2. İleti değişim modelinizi destekleyen bir kanal fabrikası<xref:System.ServiceModel.Channels.IChannelFactory> ve <xref:System.ServiceModel.Channels.IChannelListener>dinleyicisi (ve) oluşturun. Fabrika geliştirme hakkında ayrıntılar için bkz [. istemci: Kanal fabrikaları ve](client-channel-factories-and-channels.md)kanalları. Dinleyicileri geliştirme hakkında ayrıntılar için bkz [. hizmet: Kanal dinleyicileri ve kanalları](service-channel-listeners-and-channels.md).  
  
3. Ağa özgü özel durumların ya da <xref:System.TimeoutException?displayProperty=nameWithType> uygun türetilmiş <xref:System.ServiceModel.CommunicationException>sınıfına normalleştirildiğinden emin olun. Ayrıntılar için bkz. [özel durumları ve hataları işleme](handling-exceptions-and-faults.md).  
  
4. Uygulama katmanından kullanımı etkinleştirmek için, özel kanalı bir kanal <xref:System.ServiceModel.Channels.BindingElement> yığınına ekleyen bir ekleyin. Daha fazla bilgi için, bkz. [BindingElement oluşturma](creating-a-bindingelement.md).  
  
 Uygulama katmanında daha kapsamlı destek sağlamak için aşağıdaki ek adımlar gereklidir:  
  
1. Yeni bağlama öğesini yapılandırma sistemine göstermek için bağlama öğesi uzantısı bölümü ekleyin. Daha fazla bilgi için bkz. [yapılandırma ve meta veri desteği](configuration-and-metadata-support.md).  
  
2. Diğer uç noktalara iletişim kurmak için meta veri uzantıları ekleyin. Daha fazla bilgi için bkz. [yapılandırma ve meta veri desteği](configuration-and-metadata-support.md).  
  
3. İyi tanımlanmış bir profile göre bağlama öğeleri yığınını önceden yapılandıran bir bağlama ekleyin. Daha fazla bilgi için bkz. [Kullanıcı Tanımlı Bağlamalar Oluşturma](creating-user-defined-bindings.md).  
  
4. Yapılandırma sistemine bağlamayı göstermek için bağlama bölümü ve bağlama yapılandırma öğesi ekleyin. Daha fazla bilgi için bkz. [yapılandırma ve meta veri desteği](configuration-and-metadata-support.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlamaları Genişletme](extending-bindings.md)
