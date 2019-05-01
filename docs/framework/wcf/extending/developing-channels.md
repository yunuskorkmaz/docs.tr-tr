---
title: Geliştirme Kanalları
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: 44fb0da52c60b900c41b7b497861c12ed72d8ffc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858071"
---
# <a name="developing-channels"></a>Geliştirme Kanalları
Windows Communication Foundation (WCF) ile kullanılabilecek bir protokolü veya taşıma kanalı geliştirmek için uygulama katmanı birkaç adım gerektirir. Bu konuda, bu adımları açıklar ve daha fazla bilgi için belirli konulara gösterir. Kanal modeli ve bu konunun başlarında bahsedilen çeşitli türlerini anlamak için bkz: [kanal modeline genel bakış](../../../../docs/framework/wcf/extending/channel-model-overview.md). Tam aktarım kanal örnek için bkz [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).  
  
## <a name="the-channel-development-task-list"></a>Kanal geliştirme görev listesi  
 Kullanıcı tanımlı bir kanal oluşturmak için adımlar aşağıdaki gibidir. Tüm kanalları gerekir:  
  
1. Kanal iletisi Exchange desenleri karar verebilirsiniz (<xref:System.ServiceModel.Channels.IOutputChannel>, <xref:System.ServiceModel.Channels.IInputChannel>, <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IRequestChannel>, veya <xref:System.ServiceModel.Channels.IReplyChannel>), <xref:System.ServiceModel.Channels.IChannelFactory> ve <xref:System.ServiceModel.Channels.IChannelListener> , sessionful destekleyip yanı sıra destekleyecektir Bu arabirimler çeşidi. Ayrıntılar için bkz [ileti değişim deseni seçme](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md).  
  
2. Bir kanal fabrikası ve dinleyici oluşturun (<xref:System.ServiceModel.Channels.IChannelFactory> ve <xref:System.ServiceModel.Channels.IChannelListener>), ileti değişim deseni desteği. Fabrikaları geliştirme hakkında daha fazla ayrıntı için bkz. [istemci: Kanal fabrikaları ve kanallar](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md). Dinleyicileri geliştirme hakkında daha fazla ayrıntı için bkz. [hizmeti: Kanal dinleyicileri ve kanallar](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md).  
  
3. Ağ özgü özel durumların ya da normalleştirilir olun <xref:System.TimeoutException?displayProperty=nameWithType> veya uygun türetilmiş sınıf <xref:System.ServiceModel.CommunicationException>. Ayrıntılar için bkz [özel durum işleme ve hataları](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
4. Uygulama katmanı kullanımdan etkinleştirmek için eklemeniz bir <xref:System.ServiceModel.Channels.BindingElement> , özel kanal için bir kanal yığını ekler. Daha fazla bilgi için [BindingElement oluşturma](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md).  
  
 Uygulama katmanındaki daha eksiksiz desteğini etkinleştirmek için aşağıdaki ek adımlar gereklidir:  
  
1. Yeni bağlama öğesi yapılandırma sistemi için kullanıma sunmak için bir bağlama öğesi uzantısı bölümü ekleyin. Daha fazla bilgi için [yapılandırma ve meta veri desteği](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
2. Diğer uç nokta Özellikleri iletişim kurmak için meta verileri uzantılar ekleyin. Daha fazla bilgi için [yapılandırma ve meta veri desteği](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
3. İyi tanımlanmış bir profili göre bağlama öğeleri yığınını önceden yapılandırır bir bağlaması ekleyin. Daha fazla bilgi için [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
4. Bir bağlama bölümü ve bağlama yapılandırma sistemi kullanıma sunmak için bağlama yapılandırma öğesi ekleyin. Daha fazla bilgi için [yapılandırma ve meta veri desteği](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlamaları Genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)
