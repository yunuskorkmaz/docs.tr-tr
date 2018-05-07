---
title: Geliştirme Kanalları
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: def60ec0cce8da71e7e2d98ff456420949360aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="developing-channels"></a>Geliştirme Kanalları
Windows Communication Foundation (WCF) ile kullanılabilir protokolü veya taşıma kanal geliştirmek için uygulama katmanı birkaç adımı gerektirir. Bu konu, bu adımları açıklar ve daha fazla bilgi için belirli konular işaret eder. Kanal modeli ve bu konuda açıklanan çeşitli türlerini anlamak için bkz: [kanal modeli genel bakış](../../../../docs/framework/wcf/extending/channel-model-overview.md). Tam aktarım kanal örnek için bkz [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).  
  
## <a name="the-channel-development-task-list"></a>Kanal geliştirme görev listesi  
 Kullanıcı tanımlı bir kanal oluşturmak için adımlar aşağıdaki gibidir. Tüm kanalları gerekir:  
  
1.  İleti Exchange desenleri kanalının karar (<xref:System.ServiceModel.Channels.IOutputChannel>, <xref:System.ServiceModel.Channels.IInputChannel>, <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IRequestChannel>, veya <xref:System.ServiceModel.Channels.IReplyChannel>), <xref:System.ServiceModel.Channels.IChannelFactory> ve <xref:System.ServiceModel.Channels.IChannelListener> , sessionful destekleyip yanı sıra destekleyecek Bu arabirimleri çeşidi. Ayrıntılar için bkz [bir ileti değişim deseni seçin](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md).  
  
2.  Bir kanal fabrikası ve dinleyici oluşturun (<xref:System.ServiceModel.Channels.IChannelFactory> ve <xref:System.ServiceModel.Channels.IChannelListener>) ileti değişim deseni destekler. Oluşturucuları geliştirme hakkında daha fazla bilgi için bkz: [istemci: kanal fabrikaları ve kanallar](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md). Dinleyicileri geliştirme hakkında daha fazla bilgi için bkz: [hizmet: kanal dinleyicileri ve kanallar](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md).  
  
3.  Ağa özgü özel durumlar ya da normalleştirilmiş emin olun <xref:System.TimeoutException?displayProperty=nameWithType> veya uygun türetilmiş sınıf <xref:System.ServiceModel.CommunicationException>. Ayrıntılar için bkz [özel durum işleme ve hataları](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
4.  Uygulama katmanı kullanımdan etkinleştirmek için add bir <xref:System.ServiceModel.Channels.BindingElement> , özel kanalda bir kanal yığınına ekler. Daha fazla bilgi için bkz: [BindingElement oluşturma](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md).  
  
 Uygulama katmanı daha kapsamlı desteğini etkinleştirmek için aşağıdaki ek adımları gereklidir:  
  
1.  Yapılandırma sistemi için yeni bir bağlama öğesi kullanıma sunmak için bir bağlama öğesi uzantısı bölümü ekleyin. Daha fazla bilgi için bkz: [yapılandırma ve meta verileri desteği](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
2.  Diğer uç noktalara Özellikleri iletişim kurmak için meta verileri uzantıları ekleyin. Daha fazla bilgi için bkz: [yapılandırma ve meta verileri desteği](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
3.  Bağlama öğeleri iyi tanımlanmış bir profili göre yığınını önceden yapılandırır bir bağlaması ekleyin. Daha fazla bilgi için bkz: [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
4.  Bir bağlama bölümü ve yapılandırma sistemi bağlamayı kullanıma sunmak için bağlama yapılandırma öğesi ekleyin. Daha fazla bilgi için bkz: [yapılandırma ve meta verileri desteği](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlamaları Genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)
